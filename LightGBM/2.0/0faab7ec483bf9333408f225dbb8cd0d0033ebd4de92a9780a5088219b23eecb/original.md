```
loadmodel!(estimator, filename)
```

Load the fitted model `filename` into `estimator`. Note that this only loads the fitted model—not the parameters or data of the estimator whose model was saved as `filename`.

# Arguments

  * `estimator::LGBMEstimator`: the estimator to use in the prediction.
  * `filename::String`: the name of the file that contains the model.
