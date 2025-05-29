```
absolute_error(c, d, p=2)
```

Compute the absolute error between `c` and `d` with norm `p`, defined as

$\mathrm{abs \, error} = \left ( L^{-1} \int_{-L}^0 |c-d|^p \, \mathrm{d} z \right )^(1/p)$.

When `c` and `d` are on different grids, `d` is interpolated to the same grid as `c`.
