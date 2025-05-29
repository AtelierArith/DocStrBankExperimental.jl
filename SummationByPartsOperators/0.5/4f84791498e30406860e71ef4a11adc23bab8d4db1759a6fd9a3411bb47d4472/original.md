```
FourierDerivativeOperator(xmin::T, xmax::T, N::Integer) where {T<:Real}
```

Construct the `FourierDerivativeOperator` on a uniform grid between `xmin` and `xmax` using `N` nodes and `N÷2+1` complex Fourier modes.

See also [`fourier_derivative_operator`](@ref).
