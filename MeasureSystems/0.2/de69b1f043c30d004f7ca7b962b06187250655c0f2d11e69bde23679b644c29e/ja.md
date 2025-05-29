```Julia
radiationdensity(U::UnitSystem) = 𝟐^2*stefan(U)/lightspeed(U)
nonstandard : [FL⁻²Θ⁻⁴], [FL⁻²Θ⁻⁴], [ML⁻¹T⁻²Θ⁻⁴], [ML⁻¹T⁻²Θ⁻⁴], [ML⁻¹T⁻²Θ⁻⁴]
FL⁻²Θ⁻⁴⋅(τ²2⁻²3⁻¹5⁻¹ = 0.6579736267392905) [kB⁴ħ⁻³𝘤⁻³ϕ⁻³] Unified
```

黒体放射の放射密度定数 (J⋅m⁻³⋅K⁻⁴ または lb⋅ft⁻²⋅°R⁻⁴)。

```Julia
julia> radiationdensity(Metric) # J⋅m⁻³⋅K⁻⁴
kB⁴NA⁴𝘩⋅𝘤⁻⁷R∞⁴α⁻⁸μₑᵤ⁻⁴τ⁵2¹⁴3⁻¹5¹¹ = 7.5657332399(93) × 10⁻¹⁶ [J⋅m⁻³K⁻⁴] Metric

julia> radiationdensity(SI2019) # J⋅m⁻³⋅K⁻⁴
kB⁴𝘩⁻³𝘤⁻³τ⁵2⁻²3⁻¹5⁻¹ = 7.565733250280007×10⁻¹⁶ [J⋅m⁻³⋅K⁻⁴] SI2019

julia> radiationdensity(Conventional) # J⋅m⁻³⋅K⁻⁴
kB⁴NA⁴𝘤⁻⁷R∞⁴α⁻⁸μₑᵤ⁻⁴RK90⁻¹KJ90⁻²τ⁵2¹⁶3⁻¹5¹¹ = 7.5657317605(93) × 10⁻¹⁶ [J⋅m⁻³⋅K⁻⁴] Conventional

julia> radiationdensity(CODATA) # J⋅m⁻³⋅K⁻⁴
𝘤⁻⁷R∞⁴α⁻⁸μₑᵤ⁻⁴RK⁻¹KJ⁻²Rᵤ2014⁴τ⁵2¹⁶3⁻¹5¹¹ = 7.565723(17) × 10⁻¹⁶ [J⋅m⁻³⋅K⁻⁴] CODATA

julia> radiationdensity(International) # J⋅m⁻³⋅K⁻⁴
kB⁴NA⁴𝘩⋅𝘤⁻⁷R∞⁴α⁻⁸μₑᵤ⁻⁴Ωᵢₜ⋅Vᵢₜ⁻²τ⁵2¹⁴3⁻¹5¹¹ = 7.5644848940(93) × 10⁻¹⁶ [J⋅m⁻³⋅K⁻⁴] International
```
