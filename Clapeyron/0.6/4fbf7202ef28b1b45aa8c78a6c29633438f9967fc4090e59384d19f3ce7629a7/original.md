```
PPDSIdeal <: PPDSIdealModel

PPDSIdeal(components;
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## Input parameters

  * `A`: Single Parameter (`Float64`) - Model Coefficient
  * `B`: Single Parameter (`Float64`) - Model Coefficient
  * `C`: Single Parameter (`Float64`) - Model Coefficient
  * `D`: Single Parameter (`Float64`) - Model Coefficient
  * `E`: Single Parameter (`Float64`) - Model Coefficient
  * `F`: Single Parameter (`Float64`) - Model Coefficient
  * `G`: Single Parameter (`Float64`) - Model Coefficient
  * `Mw`: Single Parameter (`Float64`) (Optional) - Molecular Weight `[g/mol]`

## Description

PPDS Ideal Model:

```
Cpᵢ(T)/R = B + (C - B)y²[1 + (y − 1)(D + Ey + Fy² + Gy³)]
y = T/(A + T)
```

## Model Construction Examples

```
# Using the default database
idealmodel = PPDSIdeal("water") #single input
idealmodel = PPDSIdeal(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
idealmodel = PPDSIdeal(["neon","hydrogen"]; userlocations = ["path/to/my/db","alylee.csv"])

# Passing parameters directly
idealmodel = PPDSIdeal(["water","carbon dioxide"];
                        userlocations = (A = [4.004, 3.5],
                        B = [0.01, 2.044],
                        C = [268.8, 919.3],
                        D = [0.99, -1.06],
                        E = [1141.4, -865.1],
                        F = [3.07, 2.034],
                        G = [2507.37, 483.55],
                        H = [0.0, 0.0139],
                        I = [0.0, 341.11])
                        )
```

## References

1. Gmehling, J., Kleiber, M., Kolbe, B., & Rarey, J. (2019). Chemical thermodynamics for process simulation (2nd ed.). Berlin, Germany: Blackwell Verlag.
