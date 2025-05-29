```
CladoTree <: AbstractTree

CladoTree() :: CladoTree
CladoTree(nodes::AbstractVector{CladoNode}) :: CladoTree
CladoTree(tree::CladoTree) :: CladoTree
CladoTree(tree::ChronoTree) :: CladoTree
```

Type for cladograms or undated phylogenetic trees, assumed to be rooted,  comprising [`CladoNode`](@ref) instances. 

When called with no arguments, the constructor returns an empty `CladoTree`.

A [`ChronoTree`](@ref) can be converted to a `CladoTree` by removing all  information about time.
