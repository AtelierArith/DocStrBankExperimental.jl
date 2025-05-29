```
modpar(mp::ModPar{T}; kwargs...) where {T <: Model}
```

## Arguments

  * `mp::ModPar{T}`: Existing model parameters to be changed.
  * `kwargs`: Arbitrary number of keyword arguments.

## Returns

  * Instance of type `<: ModPar{T}`.

## Remarks

  * Note that the argument `mp` is *not* modified.
