```julia
sigsuspend(mask)
```

temporarily replaces the signal mask of the calling process with the mask given by `mask` and then suspends the process until delivery of a signal whose action is to invoke a signal handler or to terminate a process.

If the signal terminates the process, then `sigsuspend` does not return.  If the signal is caught, then `sigsuspend` returns after the signal handler returns, and the signal mask is restored to the state before the call to `sigsuspend`.

It is not possible to block `IPC.SIGKILL` or `IPC.SIGSTOP`; specifying these signals in mask, has no effect on the process's signal mask.
