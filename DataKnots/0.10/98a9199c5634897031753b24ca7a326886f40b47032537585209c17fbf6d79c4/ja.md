```
Take(N) :: Query
```

このクエリは入力の最初の `N` 要素を保持し、残りを削除します。

```jldoctest
julia> unitknot[Lift('a':'c') >> Take(2)]
──┼───┼
1 │ a │
2 │ b │
```

`Take(-N)` は最後の `N` 要素を削除します。

```jldoctest
julia> unitknot[Lift('a':'c') >> Take(-2)]
──┼───┼
1 │ a │
```
