```
legendre_second_derivative_operator(xmin::Real, xmax::Real, N::Integer)
legendre_second_derivative_operator(; xmin::Real, xmax::Real, N::Integer)
```

Construct the `LegendreDerivativeOperator` on a uniform grid between `xmin` and `xmax` using `N` nodes and `N-1` Legendre modes.
