```
criticalvalue(cb::PlugInConfidenceBand, level::Real, Σ::AbstractMatrix)
```

Return the critical value for `cb` with confidence level `level` when the estimates have an estimated variance-covariance matrix `Σ`. For some types of plug-in confidence bands, providing the number of point estimates in place of `Σ` is sufficient.
