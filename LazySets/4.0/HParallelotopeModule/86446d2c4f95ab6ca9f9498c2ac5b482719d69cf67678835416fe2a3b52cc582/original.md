# Extended help

```
rand(::Type{HParallelotope}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### Algorithm

All numbers are normally distributed with mean 0 and standard deviation 1.

The directions matrix and offset vector are created randomly. On average there is a good chance that this resulting set is empty. We then modify the offset to ensure non-emptiness.

There is a chance that the resulting set represents an unbounded set. This implementation checks for that case and then samples a new set.
