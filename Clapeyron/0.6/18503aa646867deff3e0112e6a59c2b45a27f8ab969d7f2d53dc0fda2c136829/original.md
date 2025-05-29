```
ClausiusAlpha <: ClausiusAlphaModel

ClausiusAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * none

## Description

Cubic alpha `(α(T))` model. Default for [`Clausius`](@ref)  and [`Berthelot`]

```
αᵢ = 1/Trᵢ
Trᵢ = T/Tcᵢ
```

## Model Construction Examples

```
# Because this model does not have parameters, all those constructors are equivalent:
alpha = ClausiusAlpha()
alpha = ClausiusAlpha("water")
alpha = ClausiusAlpha(["water","carbon dioxide"])
```
