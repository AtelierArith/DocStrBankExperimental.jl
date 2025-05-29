```
RapidRoute{N} <: AbstractRoute
```

Implements the RAPID (Routing Application for Parallel computatIon of Discharge) routing model.

# Fields

  * `adjacency::AbstractMatrix`: Sparse matrix representing the river network connectivity (upstream to downstream).
  * `infos::NamedTuple`: Metadata including standard variable names (`inputs`, `outputs`, `states`, `params`). States are typically `[:discharge]`. Params are `[:rapid_k, :rapid_x]`.

# Constructor

```julia
RapidRoute(; network::AbstractGraph, name::Union{Symbol, Nothing}=nothing)
```

  * `network`: A `Graphs.jl` compatible directed graph representing the river network.
  * `name`: Optional symbol identifier.

# Notes

  * Uses the Muskingum-Cunge method formulated for efficient matrix operations.
  * Suitable for large-scale river networks.
  * Parameters `k` (wave celerity) and `x` (diffusion) are expected per node via the `params` argument during simulation call.
