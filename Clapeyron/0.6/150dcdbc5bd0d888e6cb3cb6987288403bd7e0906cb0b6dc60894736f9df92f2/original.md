```
NoAlpha(args...) <: NoAlphaModel
```

## Input Parameters

None

## Description

Cubic alpha `(α(T))` model. Default for [`vdW`](@ref) EoS

```
αᵢ = 1 ∀ i
```

## Model Construction Examples

```
# Because this model does not have parameters, all those constructors are equivalent:
alpha = NoAlpha()
alpha = NoAlpha("water")
alpha = NoAlpha(["water","carbon dioxide"])
```
