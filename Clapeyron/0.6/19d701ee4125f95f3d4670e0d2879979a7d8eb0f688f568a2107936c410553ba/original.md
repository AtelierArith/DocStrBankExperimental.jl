```
KU(components;
idealmodel = BasicIdeal,
alpha = KUAlpha,
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
  * `Vc`: Single Parameter (`Float64`) - Critical Volume `[m^3]`
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `k`: Pair Parameter (`Float64`) (optional)
  * `l`: Pair Parameter (`Float64`) (optional)

## Model Parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `Vc`: Single Parameter (`Float64`) - Critical Volume `[m^3]`
  * `omega_a`: Single Parameter (`Float64`) - Critical Constant for a - No units
  * `omega_b`: Single Parameter (`Float64`) - Critical Constant for b - No units
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

Kumar-Upadhyay Cubic Equation of state. `Ωa` and `Ωb` are component-dependent

```
P = RT/(v-b) + a•κ(T)/((v²-1.6bv - 0.8b²)
a = Ωa(R²Tcᵢ²/Pcᵢ)
b = Ωb(R²Tcᵢ²/Pcᵢ)
Ωa = Zc[(1 + 1.6α - 0.8α²)²/((1 - α²)(2 + 1.6α))]
χ = ∛[√(1458Zc³ - 1701Zc² + 540Zc -20)/32√3Zc² - (729Zc³ - 216Zc + 8)/1728Zc³]
α = [χ + (81Zc² - 72Zc + 4)/144Zc²χ + (3Zc - 2)/12Zc]
Ωa = Zc[(1 + 1.6α - 0.8α²)²/((1 - α²)(2 + 1.6α))]
Ωb = αZc
```

## Model Construction Examples

```julia
# Using the default database
model = KU("water") #single input
model = KU(["water","ethanol"]) #multiple components
model = KU(["water","ethanol"], idealmodel = ReidIdeal) #modifying ideal model
model = KU(["water","ethanol"],alpha = TwuAlpha) #modifying alpha function
model = KU(["water","ethanol"],translation = RackettTranslation) #modifying translation
model = KU(["water","ethanol"],mixing = KayRule) #using another mixing rule
model = KU(["water","ethanol"],mixing = WSRule, activity = NRTL) #using advanced EoS+gᴱ mixing rule

# Passing a prebuilt model

my_alpha = PR78Alpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = KU(["ethane","butane"],alpha = my_alpha)

# User-provided parameters, passing files or folders
model = KU(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# User-provided parameters, passing parameters directly

model = KU(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Vc = [4.25e-5, 6.43e-5],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21]
                        k = [0. 0.18; 0.18 0.], #k,l can be ommited in single-component models.
                        l = [0. 0.01; 0.01 0.])
                    )
```

## References

1. Kumar, A., & Upadhyay, R. (2021). A new two-parameters cubic equation of state with benefits of three-parameters. Chemical Engineering Science, 229(116045), 116045. [doi:10.1016/j.ces.2020.116045](https://doi.org/10.1016/j.ces.2020.116045)
