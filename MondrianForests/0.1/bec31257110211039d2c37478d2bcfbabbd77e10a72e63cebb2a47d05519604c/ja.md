```
get_center(tree::MondrianTree{d}) where {d}
```

モンドリアンツリーのルートセルの中心点を取得します。

# 例

```jldoctest
tree = MondrianTree(2, 3.0)
get_center(tree)

# 出力
(0.5, 0.5)
```
