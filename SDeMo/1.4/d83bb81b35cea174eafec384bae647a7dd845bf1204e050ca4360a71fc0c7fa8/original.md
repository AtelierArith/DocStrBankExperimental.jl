```
crossvalidate(sdm, folds; thr = nothing, kwargs...)
```

Performs cross-validation on a model, given a vector of tuples representing the data splits. The threshold can be fixed through the `thr` keyword arguments. All other keywords are passed to the `train!` method.

This method returns two vectors of `ConfusionMatrix`, with the confusion matrix for each set of validation data first, and the confusion matrix for the training data second.
