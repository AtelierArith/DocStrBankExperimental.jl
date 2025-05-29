```
evaluate!(mach; resampling=CV(), measure=nothing, options...)
```

Estimate the performance of a machine `mach` wrapping a supervised model in data, using the specified `resampling` strategy (defaulting to 6-fold cross-validation) and `measure`, which can be a single measure or vector. Returns a [`PerformanceEvaluation`](@ref) object.

Available resampling strategies are `CV`, `Holdout`, `InSample`, `StratifiedCV` and `TimeSeriesCV`. If `resampling` is not an instance of one of these, then a vector of tuples of the form `(train_rows, test_rows)` is expected. For example, setting

```julia
resampling = [(1:100, 101:200),
              (101:200, 1:100)]
```

gives two-fold cross-validation using the first 200 rows of data.

Any measure conforming to the [StatisticalMeasuresBase.jl](https://juliaai.github.io/StatisticalMeasuresBase.jl/dev/) API can be provided, assuming it can consume multiple observations.

Although `evaluate!` is mutating, `mach.model` and `mach.args` are not mutated.

# Additional keyword options

  * `rows` - vector of observation indices from which both train and test folds are constructed (default is all observations)
  * `operation`/`operations=nothing` - One of `predict`, `predict_mean`, `predict_mode`, `predict_median`, or `predict_joint`, or a vector of these of the same length as `measure`/`measures`. Automatically inferred if left unspecified. For example, `predict_mode` will be used for a `Multiclass` target, if `model` is a probabilistic predictor, but `measure` is expects literal (point) target predictions. Operations actually applied can be inspected from the `operation` field of the object returned.
  * `weights` - per-sample `Real` weights for measures that support them (not to be confused with weights used in training, such as the `w` in `mach = machine(model, X, y, w)`).
  * `class_weights` - dictionary of `Real` per-class weights for use with measures that support these, in classification problems (not to be confused with weights used in training, such as the `w` in `mach = machine(model, X, y, w)`).
  * `repeats::Int=1`: set to a higher value for repeated (Monte Carlo) resampling. For example, if `repeats = 10`, then `resampling = CV(nfolds=5, shuffle=true)`, generates a total of 50 `(train, test)` pairs for evaluation and subsequent aggregation.
  * `acceleration=CPU1()`: acceleration/parallelization option; can be any instance of `CPU1`, (single-threaded computation), `CPUThreads` (multi-threaded computation) or `CPUProcesses` (multi-process computation); default is `default_resource()`. These types are owned by ComputationalResources.jl.
  * `force=false`: set to `true` to force cold-restart of each training event
  * `verbosity::Int=1` logging level; can be negative
  * `check_measure=true`: whether to screen measures for possible incompatibility with the model. Will not catch all incompatibilities.
  * `per_observation=true`: whether to calculate estimates for individual observations; if `false` the `per_observation` field of the returned object is populated with `missing`s. Setting to `false` may reduce compute time and allocations.
  * `logger=default_logger()` - a logger object for forwarding results to a machine learning tracking platform; see [`default_logger`](@ref) for details.
  * `compact=false` - if `true`, the returned evaluation object excludes these fields: `fitted_params_per_fold`, `report_per_fold`, `train_test_rows`.

See also [`evaluate`](@ref), [`PerformanceEvaluation`](@ref), [`CompactPerformanceEvaluation`](@ref).
