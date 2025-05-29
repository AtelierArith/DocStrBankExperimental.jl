```julia
sigpending() -> mask
```

yields the set of signals that are pending for delivery to the calling thread (i.e., the signals which have been raised while blocked).  The returned value is an instance of [`SigSet`](@ref).

See also: [`sigpending!`](@ref).
