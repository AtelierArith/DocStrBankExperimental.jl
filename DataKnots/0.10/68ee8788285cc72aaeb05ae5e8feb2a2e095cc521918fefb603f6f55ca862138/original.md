```
Group(X₁, X₂ … Xₙ) :: Query
```

This query groups the input data by the keys `X₁`, `X₂` … `Xₙ`.

```jldoctest
julia> unitknot[Lift(1:5) >> Group(isodd.(It))]
  │ #A     #B      │
──┼────────────────┼
1 │ false  2; 4    │
2 │  true  1; 3; 5 │
```
