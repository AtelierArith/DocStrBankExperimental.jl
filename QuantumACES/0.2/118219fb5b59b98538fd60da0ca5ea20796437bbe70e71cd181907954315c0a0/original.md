```
wls_optimise_weights(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; options::OptimOptions = OptimOptions())
```

Returns versions of the design `d` and circuit log-eigenvalue estimator covariance matrix `covariance_log` after optimising the shot weights with respect to the weighted least squares (WLS) figure of merit, alongside the figure of merit values at each step. The optimisation is parameterised by the [`OptimOptions`](@ref) object `options`.
