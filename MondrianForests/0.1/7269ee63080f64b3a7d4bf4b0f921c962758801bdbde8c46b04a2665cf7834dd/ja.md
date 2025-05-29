```
is_in(x::NTuple{d,Float64}, tree::MondrianTree{d}) where {d}
```

モンドリアンツリーのルートセルに点 `x` が含まれているかを確認します。

# 例

```jldoctest
x = ntuple(i -> 0.2, 2)
tree = MondrianTree(2, 3.0)
is_in(x, tree)

# 出力
true
```
