```
support(spline::Spline) -> a, b
```

If `spline` is a `BSpline`, return the interval $[a,b]$ on which the B-spline is non-zero. Otherwise, return `support(basis(spline))`.

# Examples

```jldoctest
julia> basis = BSplineBasis(3, 0:5);

julia> spline = Spline(basis, ones(7));

julia> zerospline = Spline(basis, zeros(7));

julia> support(spline)
(0, 5)

julia> support(zerospline) # even though the spline is zero everywhere
(0, 5)

julia> support(basis[4]) # for BSplines, return their actual support
(1, 4)
```
