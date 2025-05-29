```
locw(Xtrain, Ytrain, X; listnn, listw = nothing, algo, verbose = false, kwargs...)
```

Compute predictions for a given kNN model.

  * `Xtrain` : Training X-data.
  * `Ytrain` : Training Y-data.
  * `X` : X-data (m observations) to predict.

Keyword arguments:

  * `listnn` : List (vector) of m vectors of indexes.
  * `listw` : List (vector) of m vectors of weights.
  * `algo` : Function computing the model on    the m neighborhoods.
  * `verbose` : Boolean. If `true`, predicting information are printed.
  * `kwargs` : Keywords arguments to pass in function `algo`.   Each argument must have length = 1 (not be a collection).

Each component i of `listnn` and `listw` contains the indexes  and weights, respectively, of the nearest neighbors of x_i in Xtrain.  The sizes of the neighborhood for i = 1,...,m can be different.
