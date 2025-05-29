```
compare(times, volumes, models; holdouts=3, metric=mae, advanced_options...)
```

By calibrating `models` using the specified patient `times` and lesion `volumes`, compare those models using a hold-out set consisting of the last `holdouts` data points.

```julia
times = [0.1, 6.0, 16.0, 24.0, 32.0, 39.0]
volumes = [0.00023, 8.4e-5, 6.1e-5, 4.3e-5, 4.3e-5, 4.3e-5]

julia> comparison = compare(times, volumes, [gompertz, logistic])
ModelComparison with 3 holdouts:
  metric: mae
  gompertz:     2.198e-6
  logistic:     6.55e-6

julia> errors(comparison)
2-element Vector{Float64}:
 2.197843662660861e-6
 6.549858321487298e-6

julia> p = parameters(comparison)[1]  # calibrated parameter for `gompertz`
(v0 = 0.00022643603114569068, v∞ = 3.8453274218216947e-5, ω = 0.11537512108224635)

julia> gompertz(times, p)
6-element Vector{Float64}:
 0.00022643603114569068
 9.435316392754094e-5
 5.1039159299783234e-5
 4.303209015899451e-5
 4.021112910411027e-5
 3.922743006690166e-5
```

# Visualising comparisons

```julia
using Plots
plot(comparison, title="A comparison of two models")
```

# Keyword options

  * `holdouts=3`: number of time-volume pairs excluded from the end of the calibration data
  * `metric=mae`: metric applied to holdout set; the reported error on a model predicting volumes `v̂` is `metric(v̂, v)` where `v` is the last `holdouts` values of `volumes`. For example, any regression measure from StatisticalMeasures.jl can be used here. The built-in fallback is mean absolute error.
  * `iterations=TumorGrowth.iterations.(models)`: a vector of iteration counts for the calibration of `models`
  * `calibration_options`: a vector of named tuples providing keyword arguments for the `CalibrationProblem` for each model. Possible keys are: `p0`, `lower`, `upper`, `frozen`, `learning_rate`, `optimiser`, `radius`, `scale`, `half_life`, `penalty`, and keys corresponding to any ODE solver options. Keys left unspecified fall back to defaults, as these are described in the [`CalibrationProblem`](@ref) document string.

See also [`errors`](@ref), [`parameters`](@ref).
