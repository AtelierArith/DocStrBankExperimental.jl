```
Sort(X₁, X₂ … Xₙ) :: Query
```

このクエリは、入力データをキー `X₁`, `X₂` … `Xₙ` によってソートします。

```jldoctest
julia> unitknot[Lift(1:5) >> Sort(isodd.(It))]
──┼───┼
1 │ 2 │
2 │ 4 │
3 │ 1 │
4 │ 3 │
5 │ 5 │
```
