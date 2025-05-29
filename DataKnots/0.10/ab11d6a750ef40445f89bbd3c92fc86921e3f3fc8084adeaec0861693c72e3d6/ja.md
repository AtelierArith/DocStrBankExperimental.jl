```
Drop(N) :: Query
```

このクエリは、入力の最初の `N` 要素を削除し、残りを保持します。

```jldoctest
julia> unitknot[Lift('a':'c') >> Drop(2)]
──┼───┼
1 │ c │
```

`Drop(-N)` は、最後の `N` 要素を削除します。

```jldoctest
julia> unitknot[Lift('a':'c') >> Drop(-2)]
──┼───┼
1 │ b │
2 │ c │
```
