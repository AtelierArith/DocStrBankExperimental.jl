```
prune(dt::AbstractDimTree; keep::Union{Symbol,Pair{Symbol}})
```

Prune a tree to remove branches.

`keep` specifies a branch to incorprate into the tree, after it is also pruned. A `Pair` can be used to specify a branch to keep in that branch, and these may be chained as e.g. `keep=:branch => :smallbranch => :leaf`.

`prune` results in a DimTree that is completely convertable to a  [`DimStack`](@ref), as it no longer has branches with divergent dimensions.

# Example

```julia
pruned = prune(dimtree; keep=:branch => :leaf)
DimStack(pruned)
```
