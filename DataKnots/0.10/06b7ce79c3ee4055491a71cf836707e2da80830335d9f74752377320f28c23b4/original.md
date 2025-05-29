```
Sort(X₁, X₂ … Xₙ) :: Query
```

This query sorts the input data by the keys `X₁`, `X₂` … `Xₙ`.

```jldoctest
julia> unitknot[Lift(1:5) >> Sort(isodd.(It))]
──┼───┼
1 │ 2 │
2 │ 4 │
3 │ 1 │
4 │ 3 │
5 │ 5 │
```
