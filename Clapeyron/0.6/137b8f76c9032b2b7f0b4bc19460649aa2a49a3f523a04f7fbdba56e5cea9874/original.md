```
RK(components; 
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

Redlich-Kwong Equation of state.

```
P = RT/(V-Nb) + a•α(T)/(V(V+Nb))
```

## Model Construction Examples

```julia
# Using the default database
model = RK("water") #single input
model = RK(["water","ethanol"]) #multiple components
model = RK(["water","ethanol"], idealmodel = ReidIdeal) #modifying ideal model
model = RK(["water","ethanol"],alpha = Soave2019) #modifying alpha function
model = RK(["water","ethanol"],translation = RackettTranslation) #modifying translation
model = RK(["water","ethanol"],mixing = KayRule) #using another mixing rule
model = RK(["water","ethanol"],mixing = WSRule, activity = NRTL) #using advanced EoS+gᴱ mixing rule

# Passing a prebuilt model

my_alpha = SoaveAlpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = RK(["ethane","butane"],alpha = my_alpha) #this is efectively now an SRK model

# User-provided parameters, passing files or folders

# Passing files or folders
model = RK(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# User-provided parameters, passing parameters directly

model = RK(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21]
                        k = [0. 0.18; 0.18 0.], #k,l can be ommited in single-component models.
                        l = [0. 0.01; 0.01 0.])
                    )
```

## References

1. Redlich, O., & Kwong, J. N. S. (1949). On the thermodynamics of solutions; an equation of state; fugacities of gaseous solutions. Chemical Reviews, 44(1), 233–244. [doi:10.1021/cr60137a013](https://doi.org/10.1021/cr60137a013)
