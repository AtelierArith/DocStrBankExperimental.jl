```
EmpiricIdeal(components;
pure_userlocations = String[],
estimate_pure = false,
coolprop_userlocations = true,
Rgas = R̄,
verbose = false)
```

## Input parameters

  * JSON data (CoolProp and teqp format)

## Description

Instantiates the ideal part of a multi-component Empiric EoS model. `Rgas` can be used to set the value of the gas constant that is used during property calculations.

If `coolprop_userlocations` is true, then Clapeyron will try to look if the fluid is present in the CoolProp library.

If `estimate_pure` is true, then, if a JSON is not found, the pure model will be estimated, using the `XiangDeiters` model
