# Extended help

```
rand(::Type{Star}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### Algorithm

A predicate `P` can be passed directly. If `P` is `nothing` (default), we generate a random `HPolytope` of dimension `dim`.

All numbers are normally distributed with mean 0 and standard deviation 1.
