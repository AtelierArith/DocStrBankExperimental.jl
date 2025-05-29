```
fourier_derivative_operator(xmin::Real, xmax::Real, N::Integer)
fourier_derivative_operator(; xmin::Real, xmax::Real, N::Integer)
```

Construct the [`FourierDerivativeOperator`](@ref) on a uniform grid between `xmin` and `xmax` using `N` nodes and `N÷2+1` complex Fourier modes.
