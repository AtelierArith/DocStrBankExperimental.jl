```
Given(X₁, X₂ … Xₙ, Q) :: Query
```

This evaluates `Q` in a context augmented with named parameters added by a set of queries.

```jldoctest
julia> unitknot[Given(:x => 2, It.x .+ 1)]
┼───┼
│ 3 │
```
