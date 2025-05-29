```
dof_tstat(r::LocalProjectionResult)
```

Return the degrees of freedom used for computing t-statistics from estimation results. They could be different from [`dof_residual`](@ref) depending on the variance-covariance estimator.
