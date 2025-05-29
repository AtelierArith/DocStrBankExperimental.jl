# Extended help

```
rand(::Type{Hyperrectangle}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### Algorithm

All numbers are normally distributed with mean 0 and standard deviation 1. Additionally, the radius is nonnegative.
