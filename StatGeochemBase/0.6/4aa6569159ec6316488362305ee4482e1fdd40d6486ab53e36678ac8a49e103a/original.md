```julia
reversecopyat!(dest, src, tₛ::AbstractVector{Bool})
```

As `copyat!`, but also reverse the order of stored elements. 

Equivalent to `dest .= reverse(src[tₛ])`, but without inducing allocations.
