```
findnodes(tree::AbstractPhyloTree, args...; ifnot_haskey::Bool=false)
```

Return indices of tree node which all values proceed by transformation(s) `args` for a given attribute are true.
