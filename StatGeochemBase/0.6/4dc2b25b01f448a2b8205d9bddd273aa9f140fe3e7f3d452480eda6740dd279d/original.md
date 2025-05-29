```julia
copyat!(dest, src, tₛ::AbstractVector{Bool})
```

Copy from src to dest when tₛ is true. Equivalent to `dest .= src[tₛ]`, but without inducing allocations.

See also `reversecopyat!`
