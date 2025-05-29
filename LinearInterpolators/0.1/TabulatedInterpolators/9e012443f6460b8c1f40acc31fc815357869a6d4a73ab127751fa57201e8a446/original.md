```
TabulatedInterpolator([T,] [d = nothing,] ker, pos, nrows, ncols)
```

yields a linear map to interpolate with kernel `ker` along a dimension of length `ncols` to produce a dimension of length `nrows`.  The function `pos(i)` for `i ∈ 1:nrows` gives the positions to interpolate in fractional index unit along a dimension of length `ncols`.  Argument `d` is the rank of the dimension along which to interpolate when the operator is applied to a multidimensional array.  If it is unspecifed when the operator is created, it will have to be specified each time the operator is applied (see below).

The positions to interpolate can also be specified by a vector `x` as in:

```
TabulatedInterpolator([T,] [d = nothing,] ker, x, ncols)
```

to produce an interpolator whose output dimension is `nrows = length(x)`.  Here `x` can be an abstract vector.

Optional argument `T` is the floating-point type of the coefficients of the linear map.  By default, it is given by the promotion of the element type of the arguments `ker` and, if specified, `x`.

The tabulated operator, say `A`, can be applied to an argument `x`:

```
apply!(α, P::Operations, A, [d,] x, scratch, β, y) -> y
```

to overwrite `y` with `α*P(A)⋅x + β*y`.  If `x` and `y` are multi-dimensional, the dimension `d` to interpolate must be specified.
