```
BSpline(basis::BSplineBasis, index)
```

Return the `index`-th B-spline of `basis`.

# Example

```jldoctest
julia> basis = BSplineBasis(5, 1:10);

julia> BSpline(basis, 3)
BSpline{BSplineBasis{UnitRange{Int64}}}:
 basis: 13-element BSplineBasis{UnitRange{Int64}}:
  order: 5
  breakpoints: 1:10
 index: 3 (knots: [1, 1, 1, 2, 3, 4])
```
