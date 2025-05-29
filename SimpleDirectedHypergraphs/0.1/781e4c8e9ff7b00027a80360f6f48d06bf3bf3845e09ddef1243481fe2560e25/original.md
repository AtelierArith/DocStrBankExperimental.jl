```
dhg_load(
    fname::AbstractString;
    format::Abstract_HG_format = HGF_Format(),
    HType::Type{H} = DirectedHypergraph,
    T::Type{U} = Bool,
    D::Type{<:AbstractDict{Int, U}} = Dict{Int, T},
    V = Nothing,
    E = Nothing
) where {U <: Real, H <: AbstractDirectedHypergraph}
```

Loads a hypergraph from a file `fname`. The default saving format is `hgf`.

**Arguments**

  * `HType`: type of hypergraph to store data in
  * `T` : type of weight values stored in the hypergraph's adjacency matrix
  * `D` : dictionary for storing values the default is `Dict{Int, T}`
  * `V` : type of values stored in the vertices of the hypergraph
  * `E` : type of values stored in the edges of the hypergraph
