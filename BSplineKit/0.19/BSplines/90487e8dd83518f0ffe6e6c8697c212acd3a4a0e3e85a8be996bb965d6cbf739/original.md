```
nonzero_in_segment(B::AbstractBSplineBasis, n::Int) -> UnitRange{Int}
```

Returns the range of basis functions that are non-zero in a given knot segment.

The $n$-th knot segment is defined by $Ω_n = [t_n, t_{n + 1}]$.

For [`BSplineBasis`](@ref) and `RecombinedBSplineBasis`, the number of non-zero functions in any given segment is generally equal to the B-spline order $k$. This number decreases near the borders, but this is not significant when B-spline knots have multiplicity $k$ there (as is the default).

For B-spline bases, and excepting the borders, the non-zero B-splines are $\left\{ b_i \right\}_{i = n - k + 1}^{n}$. This function thus returns `(n - k + 1):N` when `B` is a `BSplineBasis`.

See also [`support`](@ref) for the inverse operation.
