SSH
===
```bash
# Instalación de openssh servidor en sistema ubuntu: suficiente para loguearse remotamente por ssh.
  sudo apt-get install openssh-server

# Logueo remoto por ssh
  ssh -p 2222 usuario@200.58.81.32

# Generar key para conexion en remoto: va a generar una clave privada y una publica .pub
# ed25519 es una solución criptográfica, implementa el algoritmo de firma digital de curva de Edwards EdDSA.
  ssh-keygen -t ed25519 -C "algun comentario"

# Copiar key ssh a servidor remoto: crea una linea en ./ssh/authorized_keys en el servidor remoto y ahora le host puede conectar sin necesidad del password del sistema operativo, sino solo con la clave del key creado.
  ssh-copy-id -p 2222 -i ~/.ssh/id_ed25519.pub usuario@200.58.81.32
  
# Iniciar conexion sin escribir contraseña.
  eval $(ssh-agent)
  ssh-add

 # Iniciar conexion sin escribir contraseña  de manera permanete. 
   vim .bashrc
   # Agregar
   alias ssha = 'eval $(ssh-agent) && ssh-add'
```


REFERENCIAS
---
Video explicativo
- https://www.youtube.com/watch?v=-Q4T9wLsvOQ&list=PLT98CRl2KxKEUHie1m24-wkyHpEsa4Y70&index=2

Documentacion ubuntu
- https://ubuntu.com/server/docs/openssh-server
