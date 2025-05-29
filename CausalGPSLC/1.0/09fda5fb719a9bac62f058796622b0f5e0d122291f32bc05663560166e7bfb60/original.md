```
gpslc(filename * ".csv")
gpslc(filename * ".csv"; hyperparams=hyperparams, priorparams=priorparams))

gpslc(DataFrame(X1=...,X2=...,T=...,Y=...,obj=...))
gpslc(DataFrame(X1=...,X2=...,T=...,Y=...,obj=...); hyperparams=hyperparams, priorparams=priorparams)
```

Run posterior inference on the input data.

Datatypes of DataFrame or CSV must follow these standards:

  * `T` (Boolean/Float64)
  * `Y` (Float64)
  * `X1...XN` (Float64...Float64)
  * `obj` (Any)

Optional parameters

  * `hyperparams::`[`HyperParameters`](@ref)=[`getHyperParameters`](@ref)`()`: Hyper parameters primarily define the high level amount of inference to perform.
  * `priorparams::`[`PriorParameters`](@ref)=[`getPriorParameters`](@ref)`()`: Prior parameters define the high level priors to draw from when constructing kernel functions and latent confounder structure.

Returns a [`GPSLCObject`](@ref) which stores the  hyperparameters, prior parameters, data, and posterior samples.
