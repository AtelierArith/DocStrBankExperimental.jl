```
nrmse_pdf(cov_eigenvalues::Vector{Float64}, nrmse_values::Vector{Float64}; epsilon::Real = 1e-5)
```

Returns the probability density function (PDF) for the normalised RMS error (NRMSE) of the gate eigenvalue estimator vector, which follows a generalised chi-squared distribution and whose covariance matrix has eigenvalues `cov_eigenvalues`, at the coordinates specified by `nrmse_values`. Does not calculate values when the normal approximation to the PDF is less than a factor of `epsilon` of its maximum value.

Calculation follows Eq. 3.2 of `Computing the distribution of quadratic forms in normal variables` by J. P. Imhof (1961).
