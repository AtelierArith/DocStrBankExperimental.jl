```
Booster
```

Data structure containing xgboost decision trees or other model objects.  `Booster` is used in all methods for training and predition.

`Booster` can only consume data from [`DMatrix`](@ref) objects but most methods can convert provided data implicitly.  Note that `Booster` does *not* store any of its input or output data.

See [`xgboost`](@ref) which is shorthand for a `Booster` constructor followed by training.

The `Booster` object records all non-default model hyper-parameters set either at construction or with [`setparam!`](@ref).  The xgboost library does not support retrieval of such parameters so these should be considered for UI purposes only, they are reported in the deafult `show` methods of the `Booster`.

## Constructors

```julia
Booster(train; kw...)
Booster(trains::AbstractVector; kw...)
```

## Arguments

  * `train`: Training data.  If not a `DMatrix` this will be passed to the `DMatrix` constructor.   For example it can be a training matrix or a training matrix, target pair.
  * `trains`: An array of objects used as training data, each of which will be passed to a `DMatrix`   constructor.

### Keyword Arguments

All keyword arguments excepting only those listed below will be interpreted as model parameters, see [here](https://xgboost.readthedocs.io/en/stable/parameter.html) for a comprehensive list. Both parameter names and their values must be provided exactly as they appear in the linked documentation.  Model parameters can also be set after construction, see [`setparam!`](@ref) and [`setparams!`](@ref).

  * `tree_method`: This parameter gets special handling.  By default it is `nothing` which uses the default   from `libxgboost` as per the documentation unless GPU arrays are used in which case it defaults to   `"gpu_hist"`.  If an explicit option is set, it will always be used.
  * `feature_names`: Sets the feature names of training data.  This will use the feature names set in the   input data if available (e.g. if tabular data was passed this will use column names).
  * `model_buffer`: A buffer (`AbstractVector{UInt8}` or `IO`) from which to load an existing booster   model object.
  * `model_file`: Name of a file from which to load an existing booster model object, see [`save`](@ref).
