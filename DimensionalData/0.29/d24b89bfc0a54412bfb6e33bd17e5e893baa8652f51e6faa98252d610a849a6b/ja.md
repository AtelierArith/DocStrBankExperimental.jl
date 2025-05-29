```
prune(dt::AbstractDimTree; keep::Union{Symbol,Pair{Symbol}})
```

ツリーを剪定して枝を削除します。

`keep`は、剪定された後にツリーに組み込む枝を指定します。`Pair`を使用して、その枝内で保持する枝を指定することができ、これらは例えば`keep=:branch => :smallbranch => :leaf`のように連鎖させることができます。

`prune`の結果は、もはや異なる次元を持つ枝がないため、完全に[`DimStack`](@ref)に変換可能なDimTreeになります。

# 例

```julia
pruned = prune(dimtree; keep=:branch => :leaf)
DimStack(pruned)
```
