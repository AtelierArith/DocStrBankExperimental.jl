```
ShomateIdeal <: ShomateIdealModel

ShomateIdeal(components; 
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## Input parameters

  * `a`: Single Parameter (`Float64`) - polynomial coefficient
  * `b`: Single Parameter (`Float64`) - polynomial coefficient
  * `c`: Single Parameter (`Float64`) - polynomial coefficient
  * `d`: Single Parameter (`Float64`) - polynomial coefficient
  * `e`: Single Parameter (optional) (`Float64`)  - polynomial coefficient for 1/T^2
  * `Mw`: Single Parameter (`Float64`) (Optional) - Molecular Weight `[g/mol]`

## Model parameters

  * `a`: Single Parameter (`Float64`) - polynomial coefficient
  * `b`: Single Parameter (`Float64`) - polynomial coefficient
  * `c`: Single Parameter (`Float64`) - polynomial coefficient
  * `d`: Single Parameter (`Float64`) - polynomial coefficient
  * `e`: Single Parameter (optional) (`Float64`)  - polynomial coefficient for 1/T^2
  * `coeffs`: Single Parameter (`NTuple{5,Float64}`)
  * `Mw`: Single Parameter (`Float64`) (Optional) - Molecular Weight `[g/mol]`

## Description

Shomate Ideal Model. Helmholtz energy obtained via integration of specific heat capacity:

```
Cpᵢ(T) = aᵢ  + bᵢT + cᵢT^2 + dᵢT^3 + eᵢT^-2
Cp(T) = ∑Cpᵢxᵢ
```

## Model Construction Examples

```
# Using the default database
idealmodel = ShomateIdeal("water") #single input
idealmodel = ShomateIdeal(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
idealmodel = ShomateIdeal(["neon","hydrogen"]; userlocations = ["path/to/my/db","shomate.csv"])

# Passing parameters directly
idealmodel = ShomateIdeal(["water","butane"];
            userlocations = (a = [32.24, 9.487], 
                        b = [0.00192, 0.3313], 
                        c = [1.06e-5, -0.0001108],
                        d = [-3.6e-9, -2.822e-9],
                        Mw = [18.01, 58.12])
                        ) #e is not used
```
