```
Linear()
```

Indicate that the corresponding axis should use linear interpolation.

# Extended help

Assuming uniform knots with spacing 1, the `i`th piece of linear b-spline implemented here is defined as follows.

```
y_i(x) = c p(x) + cp p(1-x)
```

where

```
p(δx) = x
```

and the values `cX` for `X ∈ {_, p}` are the coefficients.

Linear b-splines are naturally interpolating, and require no prefiltering; there is therefore no need for boundary conditions to be provided.

Also, although the implementation is slightly different in order to re-use the framework built for general b-splines, the resulting interpolant is just a piecewise linear function connecting each pair of neighboring data points.
