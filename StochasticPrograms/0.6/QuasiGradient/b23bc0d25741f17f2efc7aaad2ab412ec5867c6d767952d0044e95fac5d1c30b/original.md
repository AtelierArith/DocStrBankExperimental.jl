```
StepSize
```

An optimizer attribute for specifying an aggregation procedure to be used in the quasi-gradient algorithm. Options are:

  * [`Constant`](@ref):  Constant step size ?ConstantStep for parameter descriptions (default)
  * [`Diminishing`](@ref):  Diminishing step size ?DiminishingStep for parameter descriptions.
  * [`Polyak`](@ref):  Polyak step size ?PolyakStep for parameter descriptions.
  * [`BB`](@ref):  Barzilai-Borwein step size ?BBStep for parameter descriptions.
