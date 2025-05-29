```
knots(basis::BSplineBasis)
```

Return the knot sequence of the B-spline basis.

The knot sequence is the breakpoint sequence except that the first and last values are duplicated so they appear `order(basis)` times.

# Examples

```jldoctest
julia> knots(BSplineBasis(3, 0:5))
10-element BSplines.KnotVector{Int64, UnitRange{Int64}}:
 0
 0
 0
 1
 2
 3
 4
 5
 5
 5
```
