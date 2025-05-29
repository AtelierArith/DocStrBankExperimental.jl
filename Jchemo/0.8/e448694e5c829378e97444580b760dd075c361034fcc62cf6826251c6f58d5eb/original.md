```
locwlv(Xtrain, Ytrain, X; listnn, listw = nothing, algo, nlv, verbose = true, kwargs...)
```

Compute predictions for a given kNN model.

  * `Xtrain` : Training X-data.
  * `Ytrain` : Training Y-data.
  * `X` : X-data (m observations) to predict.

Keyword arguments:

  * `listnn` : List (vector) of m vectors of indexes.
  * `listw` : List (vector) of m vectors of weights.
  * `algo` : Function computing the model on    the m neighborhoods.
  * `nlv` : Nb. or collection of nb. of latent variables (LVs).
  * `verbose` : Boolean. If `true`, predicting information    are printed.
  * `kwargs` : Keywords arguments to pass in function `algo`.   Each argument must have length = 1 (not be a collection).

Same as [`locw`](@ref) but specific and much faster  for LV-based models (e.g. PLSR).
