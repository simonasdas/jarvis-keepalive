# jarvis-keepalive

Internes Wartungs-Repository (nur ein GitHub-Actions-Workflow, kein Quellcode):

- **Alle 5 Minuten** wird der JARVIS-Render-Dienst per HTTP angepingt
  (Secret `KEEPALIVE_URL`, nicht öffentlich einsehbar).
  Der Free-Plan von Render schläft nach **15 Minuten** ohne Traffic ein –
  der Ping hält den Dienst also dauerhaft wach.
- **Täglich um 04:23 UTC** committet der Workflow `ACTIVE.md`, damit GitHub
  das Repo nicht nach 60 Tagen ohne Aktivität als inaktiv markiert und die
  geplanten Workflows abschaltet.

Der Dienst verbraucht dadurch ~720 Free-Instance-Stunden pro Monat
(Renders Free-Kontingent: 750/Monat – passt).
