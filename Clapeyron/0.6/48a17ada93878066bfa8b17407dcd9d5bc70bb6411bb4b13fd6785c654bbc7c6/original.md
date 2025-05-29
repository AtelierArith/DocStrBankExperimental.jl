```
AlyLeeIdeal <: AlyLeeIdealModel

AlyLeeIdeal(components; 
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
  * `H`: Single Parameter (`Float64`) - Model Coefficient
  * `I`: Single Parameter (`Float64`) - Model Coefficient
  * `Mw`: Single Parameter (`Float64`) (Optional) - Molecular Weight `[g/mol]`

## Description

Aly-Lee Ideal Model (extended):

```
Cpᵢ(T)/R = A + B(CT⁻¹/sinh(CT⁻¹))² + D(ET⁻¹/cosh(ET⁻¹))² + F(GT⁻¹/sinh(GT⁻¹))² + H(IT⁻¹/cosh(IT⁻¹))²
```

## Model Construction Examples

```
# Using the default database
idealmodel = AlyLeeIdeal("water") #single input
idealmodel = AlyLeeIdeal(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
idealmodel = AlyLeeIdeal(["neon","hydrogen"]; userlocations = ["path/to/my/db","alylee.csv"])

# Passing parameters directly
idealmodel = AlyLeeIdeal(["water","carbon dioxide"];
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

1. Aly, F. A., & Lee, L. L. (1981). Self-consistent equations for calculating the ideal gas heat capacity, enthalpy, and entropy. Fluid Phase Equilibria, 6(3–4), 169–179. [doi:10.1016/0378-3812(81)85002-9](https://doi.org/10.1016/0378-3812(81)85002-9)
