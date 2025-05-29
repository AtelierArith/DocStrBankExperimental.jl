```
dhg_load(
    io::IO,
    T::Type{H},
    format::JSON_Format;
    T::Type{U} = Bool,
    D::Type{<:AbstractDict{Int, U}} = Dict{Int,U},
    V = Nothing,
    E = Nothing
) where {H <: AbstractDirectedHypergraph, U <: Real}
```

Loads a hypergraph from a stream `io` from `json` format.

**Arguments**

  * `T` : type of weight values stored in the hypergraph's adjacency matrix
  * `D` : dictionary for storing values the default is `Dict{Int, T}`
  * `V` : type of values stored in the vertices of the hypergraph
  * `E` : type of values stored in the edges of the hypergraph
