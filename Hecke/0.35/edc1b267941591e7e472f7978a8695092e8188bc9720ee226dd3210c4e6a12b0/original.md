```
submodules(T::TorQuadModule; kw...)
```

Return the submodules of `T` as an iterator. Possible keyword arguments to restrict the submodules:

  * `order::Int`: only submodules of order `order`,
  * `index::Int`: only submodules of index `index`,
  * `subtype::Vector{Int}`: only submodules which are isomorphic as an abelian group to `abelian_group(subtype)`,
  * `quotype::Vector{Int}`: only submodules whose quotient are isomorphic as an abelian to `abelian_group(quotype)`.
