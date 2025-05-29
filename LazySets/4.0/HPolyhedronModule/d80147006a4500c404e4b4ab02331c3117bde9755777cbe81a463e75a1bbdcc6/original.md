# Extended help

```
rand(::Type{HPolyhedron}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### Algorithm

We first create a random polytope and then for each constraint randomly (50%) decide whether to include it.
