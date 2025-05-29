```
one_sided_with_initial_spacing((x0, x1), N::Int, dx0; cluster_on_x0=true)
```

Apply a one-sided tanh stretching function but specify the spacing at the first layer. The `(x0, x1)` points represent the desired end-points, `N` is the number of points. The default option is to cluster near `x0`, but setting `cluster_on_x0=false` will cluster near `x1`.
