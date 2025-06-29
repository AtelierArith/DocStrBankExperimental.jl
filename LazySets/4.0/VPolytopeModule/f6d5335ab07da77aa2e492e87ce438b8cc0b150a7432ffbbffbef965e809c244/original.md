# Extended help

```
rand(::Type{VPolytope}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing,
     [num_vertices]::Int=-1)
```

### Input

  * `num_vertices` – (optional, default: `-1`) upper bound on the number of                   vertices of the polytope (see comment below)

### Algorithm

All numbers are normally distributed with mean 0 and standard deviation 1.

The number of vertices can be controlled with the argument `num_vertices`. For a negative value we choose a random number in the range `dim:5*dim` (except if `dim == 1`, in which case we choose in the range `1:2`).

Note that this implementation does not guarantee that the vertices are not redundant, and hence the result may have fewer vertices than specified in `num_vertices`.
