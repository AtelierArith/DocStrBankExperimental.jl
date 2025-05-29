```
one_sided_stretch((x0, x1), N::Int, α)
```

Apply a one-sided tanh stretching function. The `(x0, x1)` points represent the desired end-points, `N` is the number of points, and `α` is the stretching factor (recommended to be no more than ~10). The default option is to cluster near `x0`, but setting `cluster_on_x0=false` will cluster near `x1`
