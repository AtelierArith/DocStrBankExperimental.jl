```
A = SparseInterpolator{T=eltype(ker)}(ker, pos, grd)
```

yields a sparse linear interpolator suitable for interpolating with kernel `ker` at positions `pos` a function sampled on the grid `grd`.  Optional parameter `T` is the floating-point type of the coefficients of the operator `A`.  Call `eltype(A)` to query the type of the coefficients of the sparse interpolator `A`.

Then `y = apply(A, x)` or `y = A(x)` or `y = A*x` yield the result of interpolation array `x`.  The shape of `y` is the same as that of `pos`. Formally, this amounts to computing:

```
y[i] = sum_j ker((pos[i] - grd[j])/step(grd))*x[j]
```

with `step(grd)` the (constant) step size between the nodes of the grid `grd` and `grd[j]` the `j`-th position of the grid.
