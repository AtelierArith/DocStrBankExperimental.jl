```
RBFMachineWithKernel(; φ, features, labels, poly_deg)
```

A container holding an inner `model :: RBFModel` (or `model == nothing`). The inner model interpolates the data after calling `fit!`. An array of arrays of features is stored in the `features` field. Likewise for `labels`.  After `add_data!`, the model has to be fitted again, indicated by its field `is_valid`.

In constrast to the more general RBFModel, only one single RBF function (i.e. one set of shape parameters) should be used.
