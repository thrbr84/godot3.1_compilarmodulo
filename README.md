# Compilar Módulo: Godot 3.1.2 - stable

### Explicação
Video com a explicação completa no meu canal do Youtube: 
- https://www.youtube.com/watch?v=Exm2Em4P_nk

[![Video com a explicação](https://img.youtube.com/vi/Exm2Em4P_nk/0.jpg)](https://www.youtube.com/watch?v=Exm2Em4P_nk)


## Source da Godot: 
- https://github.com/godotengine/godot/releases
- Fazer download do source code (zip) - 3.1.2-stable


Se ainda não viu o vídeo anterior, onde mostro os primeiros passos para montar o ambiente android no Ubuntu 18, veja pelo link abaixo:

### (1) COMO PREPARAR O AMBIENTE (SDK, JAVA) - Parte 1
https://www.youtube.com/watch?v=GUXQVwFlOMg

Após estar com o ambiente preparado (SDK e JAVA), precisamos instalar o NDK e SCONS para fazer a compilação da Godot 3.1.2

----------

### (2) Download Android NDK
- https://developer.android.com/ndk/downloads?hl=pt-br
- Descompactar em /home/$USER/Android/Sdk/ndk-bundle

----------

### (3) Abrir o bashrc para incluirmos o caminho do NDK nas variáveis do ambiente
- nano ~/.bashrc
- export ANDROID_NDK_ROOT="/home/$USER/Android/Sdk/ndk-bundle"
- source ~/.bashrc

----------

### (4) Executar no terminal para aceitar as licenças do SDK manager
- /home/$USER/Android/Sdk/tools/bin/sdkmanager --licenses

----------

### (5) Instalar o SCONS
- sudo apt install scons -y
- scons --version

----------

### (6) INICIO DA COMPILAÇÃO
- Verificar se a plataforma Android está disponível
- scons platform

----------


#### [EDIT]
Só uma dica ae do nosso brother Rafael Pontes: tem um parâmetro -j "número de núcleos" para usar no comando scons abaixo. Com ele, o scons vai usar essa quantidade de núcleos do processador para paralelizar a compilação e fica incrivelmente mais rápida! Só é bom verificar quantos núcleos sua CPU tem para não colocar um número maior do que o disponível.


### (7) Fazer primeiro para RELEASE_DEBUG
- scons platform=android target=release_debug android_arch=armv7
- OBS: para limpar uma compilação e refazer ela, execute novamente os comandos scons, acrescentando o parâmetro "--clean"

----------

### (8) Após compilar com o scons, entrar no diretório JAVA da plataforma Android, para executar o gradlew
- cd platform/android/java
- ./gradlew build --rerun-tasks

----------

### (9) Repetir o processo para RELEASE
- scons platform=android target=release android_arch=armv7
- OBS: para limpar uma compilação e refazer ela, execute novamente os comandos scons, acrescentando o parâmetro "--clean"

----------

### (10) Após compilar com o scons, entrar no diretório JAVA da plataforma Android, para executar o gradlew
- cd platform/android/java
- ./gradlew build --rerun-tasks

----------

### (11) Após o build de release_debug e release, entrar no {root}/bin do source da Godot, e verificar se dois arquivos foram criados, sendo:
- release_debug.apk
- release.apk

----------

# Referência
- Baseado no trabalho do: https://github.com/Shin-NiL/godot-admob

# IDs para teste do ADMob
- https://developers.google.com/admob/android/test-ads

- Banner: ca-app-pub-3940256099942544/6300978111
- Interstitial: ca-app-pub-3940256099942544/1033173712
- Interstitial Video: ca-app-pub-3940256099942544/8691691433
- Rewarded Video: ca-app-pub-3940256099942544/5224354917
- Native Advanced: ca-app-pub-3940256099942544/2247696110
- Native Advanced Video: ca-app-pub-3940256099942544/1044960115

### ...
Vai utilizar esse código de forma comercial? Fique tranquilo pode usar de forma livre e sem precisar mencionar nada, claro que vou ficar contente se pelo menos lembrar da ajuda e compartilhar com os amigos, rs. Caso sinta no coração, considere me pagar um cafezinho :heart: -> https://ko-fi.com/thiagobruno



