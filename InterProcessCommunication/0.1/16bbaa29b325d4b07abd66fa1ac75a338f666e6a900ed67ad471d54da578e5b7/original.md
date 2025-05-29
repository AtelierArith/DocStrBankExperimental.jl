```julia
sigaction(signum) -> sigact
```

yields the current action (an instance of [`SigAction`](@ref)) taken by the process on receipt of the signal `signum`.

```julia
sigaction(signum, sigact)
```

installs `sigact` (an instance of [`SigAction`](@ref)) to be the action taken by the process on receipt of the signal `signum`.

Note that `signum` cannot be `SIGKILL` nor `SIGSTOP`.

See also [`SigAction`](@ref) and [`sigaction!`](@ref).
