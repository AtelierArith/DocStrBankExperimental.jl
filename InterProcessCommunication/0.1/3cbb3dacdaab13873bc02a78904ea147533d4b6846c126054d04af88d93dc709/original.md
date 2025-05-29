`SigSet` represents a C `sigset_t` structure.  It should be considered as *opaque*, its contents is stored as a tuple of unsigned integers whose size matches that of `sigset_t`.

Typical usage is:

```julia
sigset = SigSet()
sigset[signum] -> boolean
sigset[signum] = boolean
fill!(sigset, boolean) -> sigset
```

where `signum` is the signal number, an integer greater or equal `1` and less or equal`IPC.SIGRTMAX`.  Real-time signals have a number `signum` such that `IPC.SIGRTMIN ≤ signum ≤ IPC.SIGRTMAX`

Non-exported methods:

```julia
IPC.sigfillset!(sigset)          # same as fill!(signum, true)
IPC.sigemptyset!(sigset)         # same as fill!(signum, false)
IPC.sigaddset!(sigset, signum)   # same as sigset[signum] = true
IPC.sigdelset!(sigset, signum)   # same as sigset[signum] = false
IPC.sigismember(sigset, signum)  # same as sigset[signum]
```
