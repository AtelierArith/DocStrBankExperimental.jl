```
savemodel(estimator, filename; [num_iteration = -1])
```

Save the fitted model in `estimator` as `filename`.

# Arguments

  * `estimator::LGBMEstimator`: the estimator to use in the prediction.
  * `filename::String`: the name of the file to save the model in.
  * `num_iteration::Integer`: keyword argument that sets the number of iterations of the model that   should be saved. `< 0` for all iterations.
  * `start_iteration` : : Start index of the iteration that should be saved.
  * `feature_importance_type` : Type of feature importance,   can be C*API*FEATURE*IMPORTANCE*SPLIT or C*API*FEATURE*IMPORTANCE*GAIN
