```julia
sigaction!(signum, sigact, oldact) -> oldact
```

installs `sigact` to be the action taken by the process on receipt of the signal `signum`, overwrites `oldact` with the previous action and returns it. Arguments `sigact` and `oldact` are instances of [`SigAction`](@ref).

See [`SigAction`](@ref) and [`sigaction`](@ref) for more details.
