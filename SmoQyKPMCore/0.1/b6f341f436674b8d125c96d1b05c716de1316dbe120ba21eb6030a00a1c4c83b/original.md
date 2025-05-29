```
kpm_coefs!(
    coefs::AbstractVector{T}, func::Function, bounds,
    buf::AbstractVector{T} = zeros(T, 2*length(coefs)),
    r2rplan = FFTW.plan_r2r!(buf, FFTW.REDFT10)
) where {T<:AbstractFloat}
```

Calculate and record the Chebyshev polynomial expansion coefficients to order `M` in the vector `ceofs` for the function `func` on the interval `(bounds[1], bounds[2])`. Let `length(buf)` be the number of evenly spaced points on the interval for which `func` is evaluated when performing Chebyshev-Gauss quadrature to compute the Chebyshev polynomial expansion coefficients.
