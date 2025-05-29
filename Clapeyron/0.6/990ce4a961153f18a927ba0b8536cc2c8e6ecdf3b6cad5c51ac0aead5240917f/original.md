```
PR(components;
idealmodel = BasicIdeal,
alpha = PRAlpha,
mixing = vdW1fRule,
activity = nothing,
translation = NoTranslation,
userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
verbose = false,
reference_state = nothing)
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

Peng-Robinson Equation of state.

```
P = RT/(V-Nb) + a•α(T)/(V-Nb₁)(V-Nb₂)
b₁ = (1 + √2)b
b₂ = (1 - √2)b
```

## Model Construction Examples

```julia
# Using the default database
model = PR("water") #single input
model = PR(["water","ethanol"]) #multiple components
model = PR(["water","ethanol"], idealmodel = ReidIdeal) #modifying ideal model
model = PR(["water","ethanol"],alpha = Soave2019) #modifying alpha function
model = PR(["water","ethanol"],translation = RackettTranslation) #modifying translation
model = PR(["water","ethanol"],mixing = KayRule) #using another mixing rule
model = PR(["water","ethanol"],mixing = WSRule, activity = NRTL) #using advanced EoS+gᴱ mixing rule

# Passing a prebuilt model

my_alpha = PR78Alpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = PR(["ethane","butane"],alpha = my_alpha)

# User-provided parameters, passing files or folders
model = PR(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# User-provided parameters, passing parameters directly

model = PR(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21]
                        k = [0. 0.18; 0.18 0.], #k,l can be ommited in single-component models.
                        l = [0. 0.01; 0.01 0.])
                    )
```

## References

1. Peng, D.Y., & Robinson, D.B. (1976). A New Two-Constant Equation of State. Industrial & Engineering Chemistry Fundamentals, 15, 59-64. [doi:10.1021/I160057A011](https://doi.org/10.1021/I160057A011)
