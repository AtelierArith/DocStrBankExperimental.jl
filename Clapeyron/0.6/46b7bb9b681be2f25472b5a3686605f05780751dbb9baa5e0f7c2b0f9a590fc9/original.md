```
LKP <: EmpiricHelmholtzModel
LKP(components;
    idealmodel=BasicIdeal,
    verbose=false)
```

## Input parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `Vc`: Single Parameter (`Float64`) (optional) - Critical Volume `[m^3]`
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `acentricfactor`: Single Parameter (`Float64`) - Acentric Factor (no units)
  * `k`: Pair Parameter (`Float64`) (optional) - binary interaction parameter (no units)

## Input models

  * `idealmodel`: Ideal Model

## Description

Lee-Kesler-Plöker equation of state. corresponding states using interpolation between a simple, spherical fluid (methane, `∅`)  and a reference fluid (n-octane, `ref`):

```
αᵣ = (1 - ωᵣ)*αᵣ(δr,τ,params(∅)) + ωᵣ*αᵣ(δr,τ,params(ref))
τ = Tr/T
δr = Vr/V/Zr
Zr = Pr*Vr/(R*Tr)
Pr = (0.2905 - 0.085*ω̄)*R*Tr/Vr
ωᵣ = (ω̄ - ω(∅))/(ω(ref) - ω(∅))
ω̄ = ∑xᵢωᵢ
Tr = ∑xᵢ*xⱼ*Tcᵢⱼ*Vcᵢⱼ^η * (1-kᵢⱼ)
Vr = ∑xᵢ*xⱼ*Tcᵢⱼ*Vcᵢⱼ
Tcᵢⱼ = √Tcᵢ*Tcⱼ
Vcᵢⱼ = 0.125*(∛Vcᵢ + ∛Vcⱼ)^3
η = 0.25
```

## Model Construction Examples

```julia
# Using the default database
model = LKP("water") #single input
model = LKP(["water","ethanol"]) #multiple components
model = LKP(["water","ethanol"], idealmodel = ReidIdeal) #modifying ideal model

# Passing a prebuilt model

my_idealmodel = MonomerIdeal(["neon","hydrogen"];userlocations = (;Mw = [20.17, 2.]))
model =  LKP(["neon","hydrogen"],idealmodel = my_idealmodel)

# User-provided parameters, passing files or folders
model = LKP(["neon","hydrogen"]; userlocations = ["path/to/my/db","lkp/my_k_values.csv"])

# User-provided parameters, passing parameters directly

model = LKP(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Vc = [4.25e-5, 6.43e-5],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21]
                        k = [0. 0.18; 0.18 0.]) #k,l can be ommited in single-component models.
                    )
```

## References

1. Plöcker, U., Knapp, H., & Prausnitz, J. (1978). Calculation of high-pressure vapor-liquid equilibria from a corresponding-states correlation with emphasis on asymmetric mixtures. Industrial & Engineering Chemistry Process Design and Development, 17(3), 324–332. [doi:10.1021/i260067a020](https://doi.org/10.1021/i260067a020)
