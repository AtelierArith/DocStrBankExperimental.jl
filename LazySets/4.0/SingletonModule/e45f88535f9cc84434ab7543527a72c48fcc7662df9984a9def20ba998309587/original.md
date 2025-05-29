```
rand(::Type{Singleton}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### Algorithm

The element is a normally distributed vector with entries of mean 0 and standard deviation 1.
