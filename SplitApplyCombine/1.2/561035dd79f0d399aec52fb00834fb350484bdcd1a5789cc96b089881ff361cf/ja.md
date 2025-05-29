```
innerjoin(lkey, rkey, f, comparison, left, right)
```

イテラブル `left` と `right` の間でリレーショナルスタイルの結合操作を実行し、`comparison(lkey(l), rkey(r))` が `true` である要素 `f(l, r)` のコレクションを返します。ここで、`l ∈ left`、`r ∈ right` です。

# 例

```jldoctest
julia> innerjoin(iseven, iseven, tuple, ==, [1,2,3,4], [0,1,2])
6-element Array{Tuple{Int64,Int64},1}:
 (1, 1)
 (2, 0)
 (2, 2)
 (3, 1)
 (4, 0)
 (4, 2)
```
