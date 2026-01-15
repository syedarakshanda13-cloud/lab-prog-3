#include <stdio.h> #include <stdlib.h>
#include <unistd.h> // for fork(), exec(), getpid() #include <sys/wait.h> // for wait()
int main() { pid_t pid;
printf("Parent Process: PID = %d\n", getpid());
// Create a child process pid = fork();
if (pid < 0) {
// Fork failed
perror("Fork failed"); exit(1);
}
else if (pid == 0) {
// Child process block
printf("Child Process: PID = %d, Parent PID = %d\n", getpid(), getppid());
// Execute a new program (for example: "ls -l") printf("Child executing 'ls -l' command...\n"); execl("/bin/ls", "ls", "-l", NULL);
// If execl fails
perror("execl failed"); exit(1);
}
else {
printf("Parent waiting for child process to finish...\n");
 
// Wait for child termination int status;
wait(&status);
if (WIFEXITED(status)) {
printf("Child terminated normally with exit status %d\n", WEXITSTATUS(status));
} else {
printf("Child terminated abnormally.\n");
}
printf("Parent Process (PID = %d) terminating.\n", getpid());
}
return 0;
}
