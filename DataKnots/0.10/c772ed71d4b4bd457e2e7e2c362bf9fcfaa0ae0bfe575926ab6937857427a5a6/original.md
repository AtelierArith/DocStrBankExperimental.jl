```
Keep(X₁, X₂ … Xₙ) :: Query
```

`Keep` evaluates named queries, making their results available for subsequent computation.

```jldoctest
julia> unitknot[Keep(:x => 2) >> It.x]
│ x │
┼───┼
│ 2 │
```

`Keep` does not otherwise change its input.

```jldoctest
julia> unitknot[Lift(1) >> Keep(:x => 2) >> (It .+ It.x)]
┼───┼
│ 3 │
```
