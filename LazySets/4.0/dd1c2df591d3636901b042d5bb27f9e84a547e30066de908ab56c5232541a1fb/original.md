```
rand(::Type{HPOLYGON}; [N]::Type=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing,
     [num_constraints]::Int=-1) where {HPOLYGON<:AbstractHPolygon}
```

Create a random polygon in constraint representation.

### Input

  * `HPOLYGON`        – type for dispatch
  * `N`               – (optional, default: `Float64`) numeric type
  * `dim`             – (optional, default: 2) dimension
  * `rng`             – (optional, default: `GLOBAL_RNG`) random number generator
  * `seed`            – (optional, default: `nothing`) seed for reseeding
  * `num_constraints` – (optional, default: `-1`) number of constraints of the                      polygon (must be 3 or bigger; see comment below)

### Output

A random polygon in constraint representation.

### Algorithm

We create a random polygon in vertex representation and convert it to constraint representation. See [`rand(::Type{VPolygon})`](@ref). For non-flat polygons the number of vertices and the number of constraints are identical.
