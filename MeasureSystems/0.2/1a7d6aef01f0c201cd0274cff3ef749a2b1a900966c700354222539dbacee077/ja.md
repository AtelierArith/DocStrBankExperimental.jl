```Julia
loschmidt(U::UnitSystem) = atmosphere(U)/boltzmann(U)/temperature(T₀,SI2019,U)
nonstandard : [L⁻³], [L⁻³], [L⁻³], [L⁻³], [L⁻³]
L⁻³⋅(kB⁻¹R∞⁻³α⁶T₀⁻¹atm⋅τ⁻³2⁻³ = 1.5471467610(14) × 10⁻¹²) [ħ⁻³𝘤³mₑ³ϕ⁻³g₀⁻³] Unified
```

単位体積内の理想気体の分子数（数密度）（m⁻³またはft⁻³）。

```Julia
julia> loschmidt(SI2019) # m⁻³
kB⁻¹T₀⁻¹atm = 2.686780111798444×10²⁵ [m⁻³] SI2019

julia> loschmidt(Metric,atm,T₀) # m⁻³
kB⁻¹NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅T₀⁻¹atm⋅2⁻⁴5⁻³ = 2.68678011272(83) × 10²⁵ [m⁻³] Metric

julia> loschmidt(Conventional,atm,T₀) # m⁻³
kB⁻¹NA⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅T₀⁻¹atm⋅RK90⋅KJ90²2⁻⁶5⁻³ = 2.68678063809(83) × 10²⁵ [m⁻³] Conventional

julia> loschmidt(CODATA,atm,T₀) # m⁻³
𝘤⋅R∞⁻¹α²μₑᵤ⋅T₀⁻¹atm⋅RK⋅KJ²Rᵤ2014⁻¹2⁻⁶5⁻³ = 2.6867811(16) × 10²⁵ [m⁻³] CODATA

julia> loschmidt(SI1976,atm,T₀) # m⁻³
𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅T₀⁻¹atm⋅2⁻⁴5⁻³/8.31432 = 2.68682619991(83) × 10²⁵ [m⁻³] SI1976

julia> loschmidt(English) # ft⁻³
kB⁻¹ft³T₀⁻¹atm = 7.608114025223316×10²³ [ft⁻³] English

julia> loschmidt(IAU) # au⁻³
kB⁻¹au³T₀⁻¹atm = 8.99514898792(54) × 10⁵⁸ [au⁻³] IAU☉
```
