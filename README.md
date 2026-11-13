# Atualizações do INSZAPP



Este repositório usa GitHub Releases para hospedar publicamente os APKs e manifestos por HTTPS. É um host estático: não recebe eventos de instalação nem IDs de aparelhos. Como em qualquer requisição HTTPS, o GitHub pode registrar metadados de rede, como o IP.



## URL estável do feed



https://github.com/ruanmorais415-web/inszapp-updates/releases/latest/download/version.json



No ANDROID STUDIO .INSZAPP, abra a aba Feed, cole essa URL e salve. Cada nova release marcada como Latest deve conter o arquivo version.json e o APK como assets. O Atualizador verifica versão, SHA-256, pacote e assinatura e depois abre o instalador oficial do Android.



## Versão-base



A release v1.1.6 contém o INSZAPP 1.1.6, versionCode 12, código INSZ-12-DC2CCC10234D. Ela é só a base do feed e não atualiza um INSZAPP 1.1.6 já instalado.



## Como publicar uma versão futura



Passo 1: compile o mesmo pacote space.manus.papo.zapp.t069364071970706 com versionCode maior que 12.



Passo 2: para substituir instalações existentes, assine com a chave original do INSZAPP (ou uma linhagem de assinatura que o Android aceite). O APK não contém a chave privada; sem a chave original, o Android rejeita a atualização.



Passo 3: crie a release v1.1.7 e escolha o nome do APK, por exemplo INSZAPP-v1.1.7.apk.



Passo 4: no projeto do Atualizador, gere o manifesto localmente, ajustando caminho, versão e URL:



pnpm run version:manifest -- --apk ./INSZAPP-v1.1.7.apk --version-name 1.1.7 --version-code 13 --apk-url https://github.com/ruanmorais415-web/inszapp-updates/releases/download/v1.1.7/INSZAPP-v1.1.7.apk --output ./version.json



O comando calcula SHA-256 e um código INSZ-13- derivado do APK. Ele não envia o APK nem o assina.



Passo 5: anexe o APK e version.json à release v1.1.7 e publique como Latest. O endereço releases/latest/download/version.json passará a servir o manifesto novo.



Não publique como Latest até que APK, versionCode, assinatura e manifesto estejam corretos.
