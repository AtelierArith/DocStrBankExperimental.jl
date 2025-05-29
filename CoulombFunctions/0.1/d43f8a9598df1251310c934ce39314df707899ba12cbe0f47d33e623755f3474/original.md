```
coulombFs(x::AbstractVector, η, ℓ; kwargs...)
```

Convenience wrapper around [`coulombs!`](@ref) that preallocates output matrices of the appropriate dimensions, only computing the regular functions $F_\ell(\eta,x)$ and $F_\ell'(\eta,x)$.
