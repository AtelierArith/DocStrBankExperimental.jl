```
findbranches(tree::AbstractPhyloTree, args...; ifnot_haskey::Bool=false)
```

与えられた属性に対して、すべての値が変換 `args` によって真である木の枝のインデックスを返します。
