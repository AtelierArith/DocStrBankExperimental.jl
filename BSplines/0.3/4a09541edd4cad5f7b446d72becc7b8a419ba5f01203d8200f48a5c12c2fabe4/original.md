```
support(basis::BSplineBasis) -> a, b
```

Return the interval $[a,b]$ on which the B-spline basis is defined, i.e., `a` is the first and `b` the last breakpoint of the `basis`.

# Examples

```jldoctest
julia> support(BSplineBasis(3, 0:5))
(0, 5)

julia> support(BSplineBasis(4, [1.0, 1.5, 2.5, 4.0]))
(1.0, 4.0)
```
