```
M = normalized_legendre_matrix(t,n; tmin=minimum(t),tmax=maximum(t))
```

Calculates a matrix with the `n`-th order Legendre coefficients on time points `t`, a vector or range. The earliest and latest (minimum and maximum) time points will be taken from the edges of `t`. You can provide these time points, `tmin` and `tmax`, as options.

```juliadoctests
# up to 3rd order coefficients for 5 to 12
julia> M = normalized_legendre_matrix(5:12,3)

# same expression
julia> M = normalized_legendre_matrix([5,6,7,8,9,10,11,12],3)

# as above with time points ranging 1 and 15
julia> M = normalized_legendre_matrix(5:12,3, tmin=1, tmax=15)
```
