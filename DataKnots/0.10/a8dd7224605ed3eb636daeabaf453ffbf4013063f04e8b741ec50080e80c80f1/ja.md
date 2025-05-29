```
 @query dataset expr param=...
```

指定されたパラメータのセットを持つデータセットにクエリを適用します。

```jldoctest
julia> @query unitknot 2x+1 x=1
┼───┼
│ 3 │
```
