# Modelo de Text to speech (TTS).

Iniciei a tentativa de colocar text to speech nas saídas do chat bot.
Primeiro optei por usar o pyttsx3 por fora da interface, porém não funcionou.
Tentei usar dentro da interface, porém a biblioteca não conseguia salvar a resposta para conseguir tocar o áudio.
Após algumas pesquisas optei por usar o gTTS (Google Text-To-Speech) para converter o texto em áudio e então salvar como um arquivo .mp3.
Com o gTTS funcionando, comecei a explorar alternativas para tocar o áudio na hora que a mensagem fosse enviada.
Tentei usar diversas bibliotecas que funcionariam como players, mas nenhuma funcionou.
Consegui tocar a primeira resposta usando a função mixer do framework PyGame, porém encontrei o obstáculo de que o mixer mantém o arquivo carregado 
mesmo não tocando, então não consigo modificar o arquivo de áudio que vai tocar para a próxima resposta.
Descobri uma função do mixer que libera o arquivo, porém ele não funciona logo abaixo do play, eles executam ao mesmo tempo, o que não deixa i áudio com 
a resposta tocar.
Usando a biblioteca time e sua função sleep() consegui atrasar por um tempo pré-derteminado, porém como as respostas tem tamanho variado, não é ideal
Gustavo encontrou uma outra função do mixer que podemos usar em um loop para otimizar e liberar o arquivo logo depois que ele foi usado, a função 
mixer.music.get_busy().
Agora o TTS funciona perfeitamente, ele responde o input e quando termina de falar, exibe a mensagem no chat.
Fim da task.
