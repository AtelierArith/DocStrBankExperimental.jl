```
groupjoin(left, right; kw...)
groupjoin(f, left, right; kw...)
```

`left` と `right` を結合し、一致するキーを持つ値のグループを作成します。

キーワード引数のオプションについては、[`join`](@ref)を参照してください。

# 例

```
l = table([1,1,1,2], [1,2,2,1], [1,2,3,4], names=[:a,:b,:c], pkey=(:a, :b))
r = table([0,1,1,2], [1,2,2,1], [1,2,3,4], names=[:a,:b,:d], pkey=(:a, :b))

groupjoin(l, r)
groupjoin(l, r; how = :left)
groupjoin(l, r; how = :outer)
groupjoin(l, r; how = :anti)
```
