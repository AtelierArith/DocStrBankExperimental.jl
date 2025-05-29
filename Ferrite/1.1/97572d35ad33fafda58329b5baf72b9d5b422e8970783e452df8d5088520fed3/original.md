```
Grid{dim, C<:AbstractCell, T<:Real} <: AbstractGrid}
```

A `Grid` is a collection of `Ferrite.AbstractCell`s and `Ferrite.Node`s which covers the computational domain. Helper structures for applying boundary conditions or define subdomains are gathered in `cellsets`, `nodesets`, `facetsets`, and `vertexsets`.

# Fields

  * `cells::Vector{C}`: stores all cells of the grid
  * `nodes::Vector{Node{dim,T}}`: stores the `dim` dimensional nodes of the grid
  * `cellsets::Dict{String, OrderedSet{Int}}`: maps a `String` key to an `OrderedSet` of cell ids
  * `nodesets::Dict{String, OrderedSet{Int}}`: maps a `String` key to an `OrderedSet` of global node ids
  * `facetsets::Dict{String, OrderedSet{FacetIndex}}`: maps a `String` to an `OrderedSet` of `FacetIndex`
  * `vertexsets::Dict{String, OrderedSet{VertexIndex}}`: maps a `String` key to an `OrderedSet` of `VertexIndex`
