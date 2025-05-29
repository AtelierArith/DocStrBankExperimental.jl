```Julia
stefan(U::UnitSystem) = τ^5/𝟐^4*boltzmann(U)^4/(𝟑*𝟓*planck(U)^3*lightspeed(U)^2)
nonstandard : [FL⁻¹T⁻¹Θ⁻⁴], [FL⁻¹T⁻¹Θ⁻⁴], [MT⁻³Θ⁻⁴], [MT⁻³Θ⁻⁴], [MT⁻³Θ⁻⁴]
FL⁻¹T⁻¹Θ⁻⁴⋅(τ²2⁻⁴3⁻¹5⁻¹ = 0.16449340668482262) [kB⁴ħ⁻³𝘤⁻²ϕ⁻³] Unified
```

ステファン・ボルツマンの比例定数 `σ` の黒体放射 (W⋅m⁻²⋅K⁻⁴ または ?⋅ft⁻²⋅°R⁻⁴)。

```Julia
julia> stefan(SI2019) # W⋅m⁻²⋅K⁻⁴
kB⁴𝘩⁻³𝘤⁻²τ⁵2⁻⁴3⁻¹5⁻¹ = 5.670374419184431×10⁻⁸ [W⋅m⁻²K⁻⁴] SI2019

julia> stefan(Metric) # W⋅m⁻²⋅K⁻⁴
kB⁴NA⁴𝘩⋅𝘤⁻⁶R∞⁴α⁻⁸μₑᵤ⁻⁴τ⁵2¹²3⁻¹5¹¹ = 5.6703744114(70) × 10⁻⁸ [W⋅m⁻²K⁻⁴] Metric

julia> stefan(Conventional) # W⋅m⁻²⋅K⁻⁴
kB⁴NA⁴𝘤⁻⁶R∞⁴α⁻⁸μₑᵤ⁻⁴RK90⁻¹KJ90⁻²τ⁵2¹⁴3⁻¹5¹¹ = 5.6703733026(70) × 10⁻⁸ [W⋅m⁻²K⁻⁴] Conventional

julia> stefan(CODATA) # W⋅m⁻²⋅K⁻⁴
𝘤⁻⁶R∞⁴α⁻⁸μₑᵤ⁻⁴RK⁻¹KJ⁻²Rᵤ2014⁴τ⁵2¹⁴3⁻¹5¹¹ = 5.670367(13) × 10⁻⁸ [W⋅m⁻²K⁻⁴] CODATA

julia> stefan(Metric)*day(Metric)/(calorie(Metric)*100^2) # cal⋅cm⁻²⋅day⁻¹⋅K⁻⁴
kB⁴NA⁴𝘩⋅𝘤⁻⁶R∞⁴α⁻⁸μₑᵤ⁻⁴Ωᵢₜ⋅Vᵢₜ⁻²τ⁵2¹⁷5¹²43 = 0.0011701721683(14) [m⁻²K⁻⁴] Metric

julia> stefan(English) # lb⋅s⁻¹⋅ft⁻³⋅°R⁻⁴
kB⁴NA⁴𝘩⋅𝘤⁻⁶R∞⁴α⁻⁸μₑᵤ⁻⁴g₀⁻¹ft⋅lb⁻¹τ⁵2¹²3⁻⁹5¹⁵ = 3.7012656963(46) × 10⁻¹⁰ [lbf⋅ft⁻¹s⁻¹°R⁻⁴] English
```
