```
PTV(components;
idealmodel = BasicIdeal,
alpha = NoAlpha,
mixing = vdW1fRule,
activity = nothing,
translation = PTVTranslation,
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

## Description

Patel-Teja-Valderrama Equation of state.

```
P = RT/(v-b) + a•α(T)/((v - Δ₁b)*(v - Δ₂b))
aᵢᵢ = Ωaᵢ(R²Tcᵢ²/Pcᵢ)
bᵢᵢ = Ωbᵢ(R²Tcᵢ/Pcᵢ)
cᵢ = Ωcᵢ(R²Tcᵢ/Pcᵢ)
Zcᵢ = Pcᵢ*Vcᵢ/(R*Tcᵢ)
Ωaᵢ = 0.66121 - 0.76105Zcᵢ
Ωbᵢ = 0.02207 + 0.20868Zcᵢ
Ωcᵢ = 0.57765 - 1.87080Zcᵢ

γ = ∑cᵢxᵢ/∑bᵢxᵢ
δ = 1 + 6γ + γ²
ϵ = 1 + γ

Δ₁ = -(ϵ + √δ)/2
Δ₂ = -(ϵ - √δ)/2
```

## Model Construction Examples

```julia
# Using the default database
model = PTV("water") #single input
model = PTV(["water","ethanol"]) #multiple components
model = PTV(["water","ethanol"], idealmodel = ReidIdeal) #modifying ideal model
model = PTV(["water","ethanol"],alpha = TwuAlpha) #modifying alpha function
model = PTV(["water","ethanol"],translation = RackettTranslation) #modifying translation
model = PTV(["water","ethanol"],mixing = KayRule) #using another mixing rule
model = PTV(["water","ethanol"],mixing = WSRule, activity = NRTL) #using advanced EoS+gᴱ mixing rule

# Passing a prebuilt model

my_alpha = PR78Alpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = PTV(["ethane","butane"],alpha = my_alpha)

# User-provided parameters, passing files or folders
model = PTV(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# User-provided parameters, passing parameters directly

model = PTV(["neon","hydrogen"];
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

1. Valderrama, J. O. (1990). A generalized Patel-Teja equation of state for polar and nonpolar fluids and their mixtures. Journal of Chemical Engineering of Japan, 23(1), 87–91. [doi:10.1252/jcej.23.87](https://doi.org/10.1252/jcej.23.87)
