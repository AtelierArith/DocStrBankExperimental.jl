```
create_model(mp::ModPar{T}) where {T <: Model}
```

Create a new instance of model `T` with model parameters `mp`

## Remarks

  * Calls [check](@ref check) to guarantee consistency of parameters.
  * Then calls the constructor `T(mp)`, which must be implemented for each model.
