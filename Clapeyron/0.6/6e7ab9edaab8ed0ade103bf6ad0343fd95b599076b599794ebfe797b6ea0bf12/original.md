```
BasicIdeal <: IdealModel

BasicIdeal(components;
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## Input parameters

None

## Description

Default Ideal Model. Constant specific heat capacity equal to `5R/2`. it's Helmholtz energy is equal to:

```
    a₀ = A₀/nRT = ∑(xᵢlog(nxᵢ/V)) - 1 - 1.5log(T)
```

## Model Construction Examples

```
# Because this model does not have parameters, all those constructors are equivalent:
idealmodel = BasicIdeal()
idealmodel = BasicIdeal("water")
idealmodel = BasicIdeal(["water","carbon dioxide"])
```
