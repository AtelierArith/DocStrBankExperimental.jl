```
Group(X₁, X₂ … Xₙ) :: Query
```

このクエリは、入力データをキー `X₁`, `X₂` … `Xₙ` でグループ化します。

```jldoctest
julia> unitknot[Lift(1:5) >> Group(isodd.(It))]
  │ #A     #B      │
──┼────────────────┼
1 │ false  2; 4    │
2 │  true  1; 3; 5 │
```
