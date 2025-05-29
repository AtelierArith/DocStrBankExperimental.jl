```
get_volume(tree::MondrianTree{d}) where {d}
```

モンドリアンツリーのルートセルのd次元ボリュームを取得します。

# 例

```jldoctest
tree = MondrianTree(2, 3.0)
get_volume(tree)

# 出力
1.0
```
