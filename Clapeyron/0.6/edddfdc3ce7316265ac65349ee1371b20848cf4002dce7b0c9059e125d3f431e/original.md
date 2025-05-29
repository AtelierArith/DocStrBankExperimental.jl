```
NaNLiquid <: IdealModel

NaNLiquid(components; 
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## Input parameters

None

## Description

Placeholder liquid model. Returns NaN for any input.

## Model Construction Examples

```
# Because this model does not have parameters, all those constructors are equivalent:
liquid = NaNLiquid()
liquid = NaNLiquid("water")
liquid = NaNLiquid(["water","carbon dioxide"])
```
