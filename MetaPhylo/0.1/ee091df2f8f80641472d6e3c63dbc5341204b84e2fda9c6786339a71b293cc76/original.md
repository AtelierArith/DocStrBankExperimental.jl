```
distance_matrix(tree::AbstractPhyloTree, [indices::Vector{<:Integer}])
```

Return pairwise distances between all indices on the `tree` as an `AxisArray`. If not indices are specified, all leaves are used as input.
