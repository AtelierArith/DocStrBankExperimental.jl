```
get_leaf_containing(x::NTuple{d,Float64}, tree::MondrianTree{d}) where {d}
```

点 `x` を含むモンドリアンツリーの葉を取得します。

# 例

```julia
d = 2
x = ntuple(i -> 0.2, d)
tree = MondrianTree(d, 3.0)
get_leaf_containing(x, tree)
```
