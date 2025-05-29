```
XiangDeiters::SingleFluid
XiangDeiters(component;
    idealmodel = BasicIdeal,
    userlocations = String[],
    ideal_userlocations = String[],
    Rgas = nothing,
    verbose = false)
```

## Input parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `Vc`: Single Parameter (`Float64`) - Critical Volume `[m3/mol]`
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `acentricfactor`: Single Parameter (`Float64`)

## Input models

  * `idealmodel`: Ideal Model

## Description

Xiang-Deiters model. estimates a single component Empiric EoS Model from critical values and the acentric factor.

```
Zc = PcVc/RTc
θ = (Zc - 0.29)^2
aᵣ = a₀(δ,τ) + ω*a₁(δ,τ) + θ*a₂(δ,τ)
```

`Rgas` can be used to set the value of the gas constant that is used during property calculations.

## Model Construction Examples

```julia
# Using the default database
model = XiangDeiters("water") #single input
model = XiangDeiters(["water"]) #single input, as a vector
model = XiangDeiters(["water"], idealmodel = ReidIdeal) #modifying ideal model

# Passing a prebuilt model

my_idealmodel = MonomerIdeal(["ethane"])
model = XiangDeiters(["ethane"],idealmodel = my_idealmodel)

# User-provided parameters, passing files or folders
model = XiangDeiters(["hydrogen"]; userlocations = ["path/to/my/db","critical.csv"])

# User-provided parameters, passing parameters directly

model = XiangDeiters(["hydrogen"];
        userlocations = (;Tc = [44.492],
                        Pc = [2679000],
                        Vc = [4.25e-5],
                        Mw = [2.0],
                        acentricfactor = [-0.21])
                    )
```

## references

1. Xiang, H. W., & Deiters, U. K. (2008). A new generalized corresponding-states equation of state for the extension of the Lee–Kesler equation to fluids consisting of polar and larger nonpolar molecules. Chemical Engineering Science, 63(6), 1490–1496. [doi:10.1016/j.ces.2007.11.029](https://doi.org/10.1016/j.ces.2007.11.029)
