```
restrict(tree::MondrianTree{d}, time::Float64) where {d}
```

モンドリアンツリーを停止時間に制限します。

# 例

```julia
tree = MondrianTree(2, 3.0)
restrict(tree, 2.0)
```
