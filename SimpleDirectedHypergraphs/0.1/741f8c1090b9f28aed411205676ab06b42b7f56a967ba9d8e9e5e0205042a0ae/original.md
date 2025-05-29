```
dhg_load(
    io::IO,
    format::EHGF_Format;
    HType::Type{H} = DirectedHypergraph,
    T::Type{U} = Bool,
    D::Type{<:AbstractDict{Int, U}} = Dict{Int, T},
) where {U <: Real, H <: AbstractDirectedHypergraph}
```

Loads a hypergraph from a stream `io` from `ehgf` format.

**Arguments**

  * `T` : type of weight values stored in the hypergraph's adjacency matrix
  * `D` : dictionary for storing values the default is `Dict{Int, T}`

Skips a single initial comment.
