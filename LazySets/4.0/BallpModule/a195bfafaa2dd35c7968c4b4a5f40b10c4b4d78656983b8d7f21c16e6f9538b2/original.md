# Extended help

```
rand(::Type{Ballp}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### Algorithm

The center and radius are normally distributed with mean 0 and standard deviation 1. Additionally, the radius is nonnegative. The p-norm is a normally distributed number ≥ 1 with mean 1 and standard deviation 1.
