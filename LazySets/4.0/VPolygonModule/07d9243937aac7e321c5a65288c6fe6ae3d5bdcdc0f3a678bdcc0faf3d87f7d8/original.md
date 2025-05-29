# Extended help

```
rand(::Type{VPolygon}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### Input

  * `num_vertices` – (optional, default: `-1`) number of vertices of the                   polygon (see comment below)

### Notes

The number of vertices can be controlled with the argument `num_vertices`. For a negative value we choose a random number in the range `3:10`.

### Algorithm

We follow the idea described [here](https://stackoverflow.com/a/47358689) based on [Valtr95](@citet). There is also a nice video available [here](http://cglab.ca/~sander/misc/ConvexGeneration/convex.html).
