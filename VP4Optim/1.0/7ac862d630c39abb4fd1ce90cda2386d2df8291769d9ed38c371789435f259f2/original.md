```
modpar(T::Type{<: Model}; kwargs...)
```

## Arguments

  * `T::Type{<: Model}`: Type of the model to be constructed.
  * `kwargs`: Arbitrary number of keyword arguments.

## Returns

  * Instance of type `<: ModPar{T}`.

## Remarks

  * First generates default parameters with [ModPar](@ref ModPar(::Type{<: Model})) (which must be implemented for each model)
