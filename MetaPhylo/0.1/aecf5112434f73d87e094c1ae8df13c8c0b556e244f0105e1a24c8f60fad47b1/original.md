```
findbranches(tree::AbstractPhyloTree, args...; ifnot_haskey::Bool=false)
```

Return indices of tree branch which all values proceed by transformation(s) `args` for a given attribute are true.
