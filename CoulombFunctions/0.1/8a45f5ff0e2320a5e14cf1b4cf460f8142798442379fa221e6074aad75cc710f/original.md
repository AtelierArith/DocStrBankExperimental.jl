```
bessels(x::AbstractVector, nℓ; kwargs...)
```

Convenience wrapper around [`bessels!`](@ref) that preallocates output matrices of the appropriate dimensions.
