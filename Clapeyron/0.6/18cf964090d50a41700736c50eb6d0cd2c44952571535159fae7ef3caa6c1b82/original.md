```
vdW(components;
idealmodel = BasicIdeal,
alpha = NoAlpha,
mixing = vdW1fRule,
activity = nothing,
translation = NoTranslation,
userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false)
```

## Input parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `k`: Pair Parameter (`Float64`) (optional)
  * `l`: Pair Parameter (`Float64`) (optional)

## Model Parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `a`: Pair Parameter (`Float64`)
  * `b`: Pair Parameter (`Float64`)

## Input models

  * `idealmodel`: Ideal Model
  * `alpha`: Alpha model
  * `mixing`: Mixing model
  * `activity`: Activity Model, used in the creation of the mixing model.
  * `translation`: Translation Model

## Description

van der Wals Equation of state.

```
P = RT/(V-Nb) + a•α(T)/V²
```

## Model Construction Examples

```julia
# Using the default database
model = vdW("water") #single input
model = vdW(["water","ethanol"]) #multiple components
model = vdW(["water","ethanol"], idealmodel = ReidIdeal) #modifying ideal model
model = vdW(["water","ethanol"],alpha = SoaveAlpha) #modifying alpha function
model = vdW(["water","ethanol"],translation = RackettTranslation) #modifying translation
model = vdW(["water","ethanol"],mixing = KayRule) #using another mixing rule
model = vdW(["water","ethanol"],mixing = WSRule, activity = NRTL) #using advanced EoS+gᴱ mixing rule

# Passing a prebuilt model

my_alpha = SoaveAlpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = vdW(["ethane","butane"],alpha = my_alpha)

# User-provided parameters, passing files or folders

model = vdW(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# User-provided parameters, passing parameters directly

model = vdW(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21]
                        k = [0. 0.18; 0.18 0.], #k,l can be ommited in single-component models.
                        l = [0. 0.01; 0.01 0.])
                    )
```

## References

1. van der Waals JD. Over de Continuiteit van den Gasen Vloeistoftoestand. PhD thesis, University of Leiden; 1873
