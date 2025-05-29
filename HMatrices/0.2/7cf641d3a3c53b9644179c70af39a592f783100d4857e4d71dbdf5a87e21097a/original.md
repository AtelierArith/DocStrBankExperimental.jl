```
mutable struct ClusterTree{N,T}
```

Tree structure used to cluster poitns of type `SVector{N,T}` into [`HyperRectangle`](@ref)s.

# Fields:

  * `_elements::Vector{SVector{N,T}}` : vector containing the sorted elements.
  * `container::HyperRectangle{N,T}` : container for the elements in the current node.
  * `index_range::UnitRange{Int}` : indices of elements contained in the current node.
  * `loc2glob::Vector{Int}` : permutation from the local indexing system to the original (global) indexing system used as input in the construction of the tree.
  * `glob2loc::Vector{Int}` : inverse of `loc2glob` permutation.
  * `children::Vector{ClusterTree{N,T}}`
  * `parent::ClusterTree{N,T}`
