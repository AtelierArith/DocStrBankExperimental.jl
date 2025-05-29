```julia
sigwait!(mask, info, timeout=Inf) -> signum
```

behaves like [`sigwait`](@ref) but additional argument `info` is an instance of [`SigInfo`](@ref) to store the information about the accepted signal, other arguments are as for the [`sigwait`](@ref) method.
