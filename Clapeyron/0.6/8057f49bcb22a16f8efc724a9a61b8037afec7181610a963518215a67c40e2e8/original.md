```
RKPR(components;
idealmodel = BasicIdeal,
alpha = RKPRAlpha,
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
  * `Vc`: Single Parameter (`Float64`) - Critical Volume `[m3/mol]`
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `k`: Pair Parameter (`Float64`) (optional)
  * `l`: Pair Parameter (`Float64`) (optional)

## Model Parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `Vc`: Single Parameter (`Float64`) - Critical Volume `[m3/mol]`
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `a`: Pair Parameter (`Float64`)
  * `b`: Pair Parameter (`Float64`)
  * `c`: Pair Parameter (`Float64`)

## Input models

  * `idealmodel`: Ideal Model
  * `alpha`: Alpha model
  * `mixing`: Mixing model
  * `activity`: Activity Model, used in the creation of the mixing model.
  * `translation`: Translation Model

## Description

Redlich-Kwong-Peng-Robinson Equation of state.

```
P = RT/(v-b) + a•α(T)/((v + Δ₁b)*(v + Δ₂b))
Δ₁ = δ
Δ₂ = (1 - δ)/(1 + δ)
δ = ∑cᵢxᵢ

aᵢᵢ = Ωaᵢ(R²Tcᵢ²/Pcᵢ)
bᵢᵢ = Ωbᵢ(R²Tcᵢ/Pcᵢ)
Ωaᵢ = (3*yᵢ^2 + 3yᵢdᵢ + dᵢ^2 + dᵢ - 1)/(3yᵢ + dᵢ - 1)^2
Ωbᵢ = 1/(3yᵢ + dᵢ - 1)
dᵢ = (1 + cᵢ^2)/(1 + cᵢ)
yᵢ = 1 + (2(1 + cᵢ))^(1/3) + (4/(1 + cᵢ))^(1/3)
```

`cᵢ` is fitted to match:

```
if Zcᵢ[exp] > 0.29
    cᵢ = √2 - 1
else
    Zcᵢ = 1.168Zcᵢ[exp]
    f(cᵢ) == 0
    f(cᵢ) = Zcᵢ - yᵢ/(3yᵢ + dᵢ - 1)
```

## Model Construction Examples

```julia
# Using the default database
model = RKPR("water") #single input
model = RKPR(["water","ethanol"]) #multiple components
model = RKPR(["water","ethanol"], idealmodel = ReidIdeal) #modifying ideal model
model = RKPR(["water","ethanol"],alpha = TwuAlpha) #modifying alpha function
model = RKPR(["water","ethanol"],translation = RackettTranslation) #modifying translation
model = RKPR(["water","ethanol"],mixing = KayRule) #using another mixing rule
model = RKPR(["water","ethanol"],mixing = WSRule, activity = NRTL) #using advanced EoS+gᴱ mixing rule

# Passing a prebuilt model

my_alpha = PR78Alpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = RKPR(["ethane","butane"],alpha = my_alpha)

# User-provided parameters, passing files or folders
model = RKPR(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# User-provided parameters, passing parameters directly

model = RKPR(["neon","hydrogen"];
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

1. Cismondi, M., & Mollerup, J. (2005). Development and application of a three-parameter RK–PR equation of state. Fluid Phase Equilibria, 232(1–2), 74–89. [doi:10.1016/j.fluid.2005.03.020](https://doi.org/10.1016/j.fluid.2005.03.020)
2. Tassin, N. G., Mascietti, V. A., & Cismondi, M. (2019). Phase behavior of multicomponent alkane mixtures and evaluation of predictive capacity for the PR and RKPR EoS’s. Fluid Phase Equilibria, 480, 53–65. [doi:10.1016/j.fluid.2018.10.005](https://doi.org/10.1016/j.fluid.2018.10.005)
