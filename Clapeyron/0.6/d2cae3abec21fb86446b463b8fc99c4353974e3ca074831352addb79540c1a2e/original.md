```
AbbottVirial <: SecondVirialModel
AbbottVirial(components;
            idealmodel = BasicIdeal,
            userlocations = String[],
            ideal_userlocations = String[],
            verbose = false)
```

## Input parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `acentricfactor`: Single Parameter (`Float64`) - Acentric Factor
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`

## Input models

  * `idealmodel`: Ideal Model

## Description

Virial model using Corresponding State Principles:

```
B = ∑xᵢxⱼBᵢⱼ
Bᵢⱼ = BrᵢⱼRTcᵢⱼ/Pcᵢⱼ
Brᵢⱼ = B₀ + ωᵢⱼB₁
B₀ = 0.083 + 0.422/Trᵢⱼ^1.6
B₁ = 0.139 - 0.172/Trᵢⱼ^4.2
Trᵢⱼ = T/Tcᵢⱼ
Tcᵢⱼ = √TcᵢTcⱼ
Pcᵢⱼ = (Pcᵢ + Pcⱼ)/2
ωᵢⱼ = (ωᵢ + ωⱼ)/2
```

## Model Construction Examples

```julia
# Using the default database
model = AbbottVirial("water") #single input
model = AbbottVirial(["water","ethanol"]) #multiple components
model = AbbottVirial(["water","ethanol"], idealmodel = ReidIdeal) #modifying ideal model

# Passing a prebuilt model

my_idealmodel = MonomerIdeal(["neon","hydrogen"];userlocations = (;Mw = [20.17, 2.]))
model = AbbottVirial(["neon","hydrogen"],idealmodel = my_idealmodel)

# User-provided parameters, passing files or folders
model = AbbottVirial(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical.csv"])

# User-provided parameters, passing parameters directly

model = AbbottVirial(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21])
                    )
```

## References

1. Smith, H. C. Van Ness Joseph M. Introduction to Chemical Engineering Thermodynamics 4E 1987.
