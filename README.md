# Proyecto-Final---Respuesta-en-Vivo-a-Incidentes
 Live Incident Response — Servidor Linux Comprometido

Proyecto Final del Bootcamp de Ciberseguridad de 4Geeks Academy.

Investigación forense en vivo (Live Incident Response) sobre un servidor Linux en producción comprometido. El análisis se realizó sobre el sistema activo, sin apagado ni extracción de disco, priorizando la disponibilidad del servicio.

Rol: Analista de Ciberseguridad
Autor: Raúl Martín
Marco de referencia: NIST Cybersecurity Framework (CSF)


📄 Informe completo

El informe técnico detallado, con capturas y justificaciones de cada acción, está disponible aquí:

➡️ Informe_Respuesta_Incidentes_Raul_Martin.pdf


🎯 Objetivo


Inspeccionar el sistema comprometido en tiempo real.
Detectar vulnerabilidades explotadas y persistencias maliciosas.
Restaurar la integridad y disponibilidad del sistema.
Documentar todo el proceso con evidencia justificada.



🔍 Resumen de hallazgos

HallazgoSeveridadExfiltración de datos activa (/etc/passwd enviado cada 15 min a IP externa)🔴 CríticaUsuario malicioso hacker con shell interactiva🔴 CríticaCronjob de persistencia disfrazado de tarea de mantenimiento🔴 CríticaDropper de malware (install.sh → payload.bin)🟠 AltaCredenciales en texto plano en directorios ocultos🟠 AltaServicio FTP (vsftpd) inseguro expuesto🟠 AltaLogs de autenticación manipulados / corrompidos🟠 AltaHistoriales de comandos falsificados y archivos señuelo🟡 Media

Vector de entrada: acceso SSH a la cuenta sysadmin mediante fuerza bruta.


🗂️ Fases del proyecto


Reconocimiento y recolección de evidencias — investigación manual siguiendo metodología Blue Team (procesos, cronjobs, usuarios, logs, red, persistencia).
Remediación y restauración — erradicación de la amenaza y hardening del sistema.
Informe técnico final — documentación completa bajo el marco NIST CSF.



🧰 Herramientas y comandos empleados

Investigación realizada íntegramente con herramientas nativas del sistema (sin utilidades automatizadas), reforzando el criterio analítico:

ps · pstree · crontab · cat /etc/cron.d/* · grep sobre /var/log/auth.log · last · ss · iptables / ufw · find -perm · awk · systemctl

Remediación: userdel · passwd · rm · systemctl disable · edición de sshd_config · gestión de ufw.

Entorno: VirtualBox · Ubuntu 20.04 LTS · Agente Wazuh.


📁 Estructura del repositorio

.
├── README.md
└── Informe_Respuesta_Incidentes_Raul_Martin.pdf


✅ Resultado

Todos los vectores de ataque fueron identificados, la cronología del incidente reconstruida y la amenaza erradicada sin interrumpir el servicio. El sistema quedó reforzado siguiendo buenas prácticas de hardening.

