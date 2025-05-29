```
chi2(res::AbstractVector{OpticalResidual{T, U}} [,
    fit::LeastSquaresFit{T}]) where {T <: Real, U <: Number}
```

Return the chi square of `res`

$$
\chi^2 = \sum_{i=1}^m w_i \xi_i^2,
$$

where $\xi_i$ is the i-th optical residual with statistical weight $w_i$. If `fit` is given, evaluate the residuals in `fit.x`.
