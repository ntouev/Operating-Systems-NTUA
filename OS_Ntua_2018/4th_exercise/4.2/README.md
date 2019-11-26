# scheduler-shell.c
#### NEW STUFF HERE:
###### Shell implementation and interaction with the scheduler

This program is an extention of the previous one.
Now the scheduler also includes another process, the "shell". The source code is in the file shell.c and request.h has the declarations of the requests
from the shell to the scheduler.  
###### The available commands are:
* "k id": kill process
* "p exec": spawn a new process
* "p": print all processes and the current one
* "q": exit

###### Known bug (1)
If I have shell----prog(id=1)----prog(id=2)
and kill prog with id=1 then the remaining process will still have id=2.  
This needs to be fixed.

###### Known bug (2)
When all processes terminate the scheduler still schedules the shell. So in order to terminate I should type "q" to terminate the shell, or to fix it so that the shell terminates when no process is alive.

###### Usage:
eg:
* ./scheduler prog prog
* and during the execution I can use the available shell commands.

###### HOW THE SHELL WORKS:
It receives as arguments two file descriptors. One for writing requests into a