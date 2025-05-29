```
diagnose(setting; alpha = 0.5)
```

Diagnose a regression setting and report potential outliers using [`dffits`](@ref), [`dfbetas`](@ref) [`cooks`](@ref), and [`hatmatrix`](@ref)

# Arguments

  * `setting::RegressionSetting`: A regression setting object.
  * `alpha`: Alpha value for Cooks distance cutoff. See [`cooksoutliers`](@ref).
