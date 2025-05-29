```
predict(estimator, X; [num_iterations = -1, verbosity = 1,
is_row_major = false, num_threads = -1, predict_raw_score = false, predict_leaf_index = false, predict_contrib = false])
```

Return a **MATRIX** with the labels that the `estimator` predicts for features data `X`. Use `dropdims` if a vector is required.

# Arguments

  * `estimator::LGBMEstimator`: the estimator to use in the prediction.
  * `X::Union{AbstractMatrix{TX}, AbstractMatrix{Union{TX, Missing}}}`: the features data.   If `X` is of type `Union{Float, Missing}`, missing values will be replaced with `NaN`.   If `X` is of type `Int`, missing values will be replaced with `NaN` after casting to `Float64`.
  * `predict_type::Integer`: keyword argument that controls the prediction type. `0` for normal   scores with transform (if needed), `1` for raw scores, `2` for leaf indices, `3` for SHAP contributions.
  * `num_iterations::Integer`: keyword argument that sets the number of iterations of the model to   use in the prediction. `< 0` for all iterations.
  * `verbosity::Integer`: keyword argument that controls LightGBM's verbosity. `< 0` for fatal logs   only, `0` includes warning logs, `1` includes info logs, and `> 1` includes debug logs.
  * `is_row_major::Bool`: keyword argument that indicates whether or not `X` is row-major. `true`   indicates that it is row-major, `false` indicates that it is column-major (Julia's default).
  * `num_threads::Integer`: keyword argument specifying the number of threads to use   for prediction. Default is `-1` which reuses `num_threads` of the estimator.
  * `predict_raw_score::Bool`: keyword argument that indicates whether or not to predict raw scores. Setting to true overrides the estimator's setting.
  * `predict_leaf_index::Bool`: keyword argument that indicates whether or not to predict leaf indices. Setting to true overrides the estimator's setting.
  * `predict_contrib::Bool`: keyword argument that indicates whether or not to predict SHAP contributions. Setting to true overrides the estimator's setting.
