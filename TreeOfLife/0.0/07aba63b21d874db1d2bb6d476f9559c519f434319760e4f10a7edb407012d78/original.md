```
ChronoTree <: AbstractTree

ChronoTree(nodes::AbstractVector{ChronoNode}) :: ChronoTree
ChronoTree() :: ChronoTree
```

Type for chronograms or dated phylogenetic trees, assumed to be rooted,  comprising [`ChronoNode`](@ref) instances. Compare [`CladoTree`](@ref). 

When called with no arguments, the constructor returns an empty `ChronoTree`.
