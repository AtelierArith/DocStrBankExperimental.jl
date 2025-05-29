```
HierarchicalCollocationPoint{N,CP,RT} <: AbstractHierarchicalCollocationPoint{N,CP,RT}
```

A collocation point.

# Fields

`cpt::CP` : [`DistributedSparseGrids.CollocationPoint`](@ref) `children::SVector{N,SVector{2,HierarchicalCollocationPoint{N,CP,RT}}}` : Container for at most two children per dimension `parents::SVector{N,HierarchicalCollocationPoint{N,CP,RT}}` : Container for parents  `fval::RT` : Function Value `scaling_weight::RT` : Scaling Weight (function value minus l-1 level interpolator both at cpt.coords)
