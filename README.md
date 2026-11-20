[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e00aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24153993&assignment_repo_type=AssignmentRepo)

## Ejecutar la consola

Desde PowerShell:

```powershell
Set-ExecutionPolicy -Scope Process Bypass
.\ejecutar-consola.ps1
```

El lanzador descarga las dependencias ausentes, compila las clases y ejecuta
`proyectomailgrupo01sa.Consola`. Durante la ejecución muestra en tiempo real
los comandos y respuestas de los sockets POP3 y SMTP, incluyendo `HELO`,
`MAIL FROM`, `RCPT TO`, `DATA` y `QUIT`, además del remitente y subject de
cada mensaje recibido.

Al iniciar, la consola también muestra el estado de PostgreSQL, SMTP, POP3 e
IMAP, incluyendo el host, puerto, saludo del servidor o el error de conexión.

## Probar sin servidor del docente (Docker + GreenMail)

Este modo no cambia la lógica del sistema: solo cambia host/puertos/credenciales
de correo por variables de entorno.

1) Iniciar entorno local y ejecutar la consola:

```powershell
Set-ExecutionPolicy -Scope Process Bypass
.\ejecutar-consola-local-docker.ps1
```

2) En otra terminal, enviar un comando de prueba al buzón local:

```powershell
.\enviar-comando-prueba.ps1 -Subject "usuario listar"
```

Opcionalmente puedes enviar otros comandos:

```powershell
.\enviar-comando-prueba.ps1 -Subject "help"
.\enviar-comando-prueba.ps1 -Subject "grupo listar"
```

3) Para apagar GreenMail:

```powershell
docker compose -f .\docker-compose.greenmail.yml down
```
