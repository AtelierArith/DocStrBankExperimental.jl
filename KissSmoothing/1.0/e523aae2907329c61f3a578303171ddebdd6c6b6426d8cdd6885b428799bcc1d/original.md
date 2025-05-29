```
fit_nspline(xv::Vector, yv::Vector, cp::Vector)
```

fit natural cubic splines basis function according to:

```
`xv` : array N, N number of training points

`yv` : array N, N number of training points

`cp` : array K, K number of control points
```

returns a callable function.
