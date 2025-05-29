```
leftgroupjoin(lkey, rkey, f, comparison, left, right)
```

`lkey(l)`でラベル付けされたグループのコレクションを作成し、各グループには`comparison(lkey(l), rkey(r))`を満たす要素`f(l, r)`が含まれます。一致するものがない場合でも、グループは作成されます（空のコレクションで）。

この操作は、SQLの左外部結合にいくつかの類似点があります。

### 例

```jldoctest
julia> leftgroupjoin(iseven, iseven, tuple, ==, [1,2,3,4], [0,1,2])
Dictionary{Bool,Array{Tuple{Int64,Int64},1}} with 2 entries:
  false │ Tuple{Int64,Int64}[(1, 1), (3, 1)]
  true  │ Tuple{Int64,Int64}[(2, 0), (2, 2), (4, 0), (4, 2)]
```
