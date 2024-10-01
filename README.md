# Pasos para realizar los experimentos

## Crear un codespaces:

![codespaces](https://github.com/user-attachments/assets/97d7b532-42c4-4a97-a0d3-b8ff335b0ebe)

## Servidores

El proyecto cuenta con dos servidores. Un servidor web y un servidor 
que gestiona la conexión socket.io (websocket). La tarea del servidor web es enviar dos 
posibles sitios. Un sitio móvil y un sitio para escritorio. El sitio 
móvil leerá la posición x,y del sensor touch y la enviará al sitio 
de escritorio. Con esta información se colocará la posición 
en un círculo en el sitio de escritorio. La comunicación entre los 
dos sitios se realizará mediante socket.io.

* El archivo server.js contiene el código de los servidores.
* En la carpeta public están los dos sitios web que estarán.

Los pasos para ejecutar la aplicación son:

* Clonar el repositorio en codespaces.
* Ejecutar npm install
* Ejecutar npm start
* Leer la url que expondrá Github para contar remotamente los clientes.

![image](https://github.com/user-attachments/assets/a6ad0e38-a74c-4219-970d-ceb4474b5321)

En este caso sería (para este ejemplo, en tu caso serán distintas):

``` js
https://probable-fiesta-q9q4pjvqq73949w-8080.app.github.dev/:8080
``` 

* Detener el servidor (con la combinación CTRL+C en la terminal)
* Modificar la URL del socketUrl en cada aplicación: mobile, desktop.
* npm start
* En los clientes las aplicaciones web estarían corriendo en (para este ejemplo, en tu caso serán distintas):

``` js
https://probable-fiesta-q9q4pjvqq73949w-8080.app.github.dev/desktop/index.html
https://probable-fiesta-q9q4pjvqq73949w-8080.app.github.dev/mobile/index.html
```

## Sitios web

No olvides modificar el archivo sketch.js para el sitio desktop y mobile en esta parte 
del código:

``` js
    //let socketUrl = 'http://localhost:3000';
    let socketUrl = 'https://probable-fiesta-q9q4pjvqq73949w-8080.app.github.dev';
    socket = io(socketUrl); 
```

Nota que la línea localhost está comentada. Esta línea permite hacer pruebas locales 
en caso de que tengas un computador con WiFi. Ten presente que la aplicación en tu 
móvil se conectará a tu computador y por tanto necesitarás conocer la dirección 
IP de este. Eso lo haces abriendo el símbolo del sistema de windows y escribiendo 
el comando:

``` bash
ipconfig
```
En mi caso busco:

Wireless LAN adapter Wi-Fi:
IPv4 Address. . . . . . . . . . . : 192.168.1.17

Y en el archivo sketch.js de la aplicación móvil haría la siguiente modificación

``` js
    let socketUrl = 'http://192.168.1.17:3000';
    //let socketUrl = 'https://probable-fiesta-q9q4pjvqq73949w-8080.app.github.dev';
    socket = io(socketUrl);
```

> [!WARNING]  
> Una vez termines de hacer las pruebas NO OLVIDES detener el servidor



