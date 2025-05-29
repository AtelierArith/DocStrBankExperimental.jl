# Extended help

```
rand(::Type{HPolytope}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### Input

  * `num_vertices` – (optional, default: `-1`) upper bound on the number of                   vertices of the polytope (see comment below)

### Algorithm

If `num_vertices == 0`, we create a fixed infeasible polytope (corresponding to the `EmptySet`).

If `num_vertices == 1`, we create a random `Singleton` and convert it.

If `dim == 1`, we create a random `Interval` and convert it.

If `dim == 2`, we create a random `VPolygon` and convert it.

Otherwise, we create a random `VPolytope` and convert it (hence also the argument `num_vertices`). See [`rand(::Type{VPolytope})`](@ref).
