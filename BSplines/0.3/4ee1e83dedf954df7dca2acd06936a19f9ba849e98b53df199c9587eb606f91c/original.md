```
order(spline::Spline)
order(basis::BSplineBasis)
```

Return the order of a spline or a B-spline basis.

# Examples

```jldoctest
julia> order(BSplineBasis(3, 0:5))
3

julia> order(BSplineBasis(4, [1.0, 1.5, 2.5, 4.0]))
4
```
