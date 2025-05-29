```
PerformanceEvaluation <: AbstractPerformanceEvaluation
```

Type of object returned by [`evaluate`](@ref) (for models plus data) or [`evaluate!`](@ref) (for machines). Such objects encode estimates of the performance (generalization error) of a supervised model or outlier detection model, and store other information ancillary to the computation.

If [`evaluate`](@ref) or [`evaluate!`](@ref) is called with the `compact=true` option, then a [`CompactPerformanceEvaluation`](@ref) object is returned instead.

When `evaluate`/`evaluate!` is called, a number of train/test pairs ("folds") of row indices are generated, according to the options provided, which are discussed in the [`evaluate!`](@ref) doc-string. Rows correspond to observations. The generated train/test pairs are recorded in the `train_test_rows` field of the `PerformanceEvaluation` struct, and the corresponding estimates, aggregated over all train/test pairs, are recorded in `measurement`, a vector with one entry for each measure (metric) recorded in `measure`.

When displayed, a `PerformanceEvaluation` object includes a value under the heading `1.96*SE`, derived from the standard error of the `per_fold` entries. This value is suitable for constructing a formal 95% confidence interval for the given `measurement`. Such intervals should be interpreted with caution. See, for example, [Bates et al.  (2021)](https://arxiv.org/abs/2104.00673).

### Fields

These fields are part of the public API of the `PerformanceEvaluation` struct.

  * `model`: model used to create the performance evaluation. In the case a   tuning model, this is the best model found.
  * `measure`: vector of measures (metrics) used to evaluate performance
  * `measurement`: vector of measurements - one for each element of `measure` - aggregating the performance measurements over all train/test pairs (folds). The aggregation method applied for a given measure `m` is `StatisticalMeasuresBase.external_aggregation_mode(m)` (commonly `Mean()` or `Sum()`)
  * `operation` (e.g., `predict_mode`): the operations applied for each measure to generate predictions to be evaluated. Possibilities are: `predict`, `predict_mean`, `predict_mode`, `predict_median`, or `predict_joint`.
  * `per_fold`: a vector of vectors of individual test fold evaluations (one vector per measure). Useful for obtaining a rough estimate of the variance of the performance estimate.
  * `per_observation`: a vector of vectors of vectors containing individual per-observation measurements: for an evaluation `e`, `e.per_observation[m][f][i]` is the measurement for the `i`th observation in the `f`th test fold, evaluated using the `m`th measure.  Useful for some forms of hyper-parameter optimization. Note that an aggregregated measurement for some measure `measure` is repeated across all observations in a fold if `StatisticalMeasures.can_report_unaggregated(measure) == true`. If `e` has been computed with the `per_observation=false` option, then `e_per_observation` is a vector of `missings`.
  * `fitted_params_per_fold`: a vector containing `fitted params(mach)` for each machine `mach` trained during resampling - one machine per train/test pair. Use this to extract the learned parameters for each individual training event.
  * `report_per_fold`: a vector containing `report(mach)` for each machine `mach` training in resampling - one machine per train/test pair.
  * `train_test_rows`: a vector of tuples, each of the form `(train, test)`, where `train` and `test` are vectors of row (observation) indices for training and evaluation respectively.
  * `resampling`: the user-specified resampling strategy to generate the train/test pairs (or literal train/test pairs if that was directly specified).
  * `repeats`: the number of times the resampling strategy was repeated.

See also [`CompactPerformanceEvaluation`](@ref).
