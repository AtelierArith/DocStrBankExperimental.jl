```
Each(X) :: Query
```

これは `X` を要素ごとに評価します。

```jldoctest
julia> X = Lift('a':'c') >> Count;

julia> unitknot[Lift(1:3) >> Each(X)]
──┼───┼
1 │ 3 │
2 │ 3 │
3 │ 3 │
```

これを `Each` なしのクエリと比較します。

```jldoctest
julia> X = Lift('a':'c') >> Count;

julia> unitknot[Lift(1:3) >> X]
┼───┼
│ 9 │
```
