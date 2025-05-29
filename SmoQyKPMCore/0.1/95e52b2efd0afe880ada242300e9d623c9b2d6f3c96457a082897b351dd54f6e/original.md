```
KPMExpansion(func::Function, bounds, M::Int, N::Int = 2*M)
```

Initialize an instance of the [`KPMExpansion`](@ref) type to approximate the univariate function `func`, called as `func(x)`, with a order `M` Chebyshev polynomial expansion on the interval `bounds[1] < x bounds[2]`. Here, `N ≥ M` is the number of points at which `func` is evaluated on that specified interval, which are then used to calculate the expansion coeffiencents via Chebyshev-Gauss quadrature.
