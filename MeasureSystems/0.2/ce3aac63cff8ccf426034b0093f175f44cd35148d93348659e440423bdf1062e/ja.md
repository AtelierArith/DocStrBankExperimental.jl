```Julia
planck(U::UnitSystem) = turn(x)*planckreduced(x)
action : [FLT], [FLT], [ML²T⁻¹], [ML²T⁻¹], [ML²T⁻¹]
FLT⋅(τ = 6.283185307179586) [ħ⋅ϕ] 統一

プランク定数 `𝘩` は電磁周波数あたりのエネルギー (J⋅s または ft⋅lb⋅s) です。

```

Julia julia> planck(SI2019) # J⋅s 𝘩 = 6.62607015×10⁻³⁴ [J⋅s] SI2019

julia> planck(SI2019)*lightspeed(SI2019) # J⋅m 𝘩⋅𝘤 = 1.9864458571489286×10⁻²⁵ [J⋅m] SI2019

julia> planck(CODATA) # J⋅s RK⁻¹KJ⁻²2² = 6.626070039(82) × 10⁻³⁴ [J⋅s] CODATA

julia> planck(Conventional) # J⋅s RK90⁻¹KJ90⁻²2² = 6.626068854361324×10⁻³⁴ [J⋅s] Conventional

julia> planck(SI2019)/elementarycharge(SI2019) # eV⋅s 𝘩⋅𝘦⁻¹ = 4.135667696923859×10⁻¹⁵ [Wb] SI2019

julia> planck(SI2019)*lightspeed(SI2019)/elementarycharge(SI2019) # eV⋅m 𝘩⋅𝘤⋅𝘦⁻¹ = 1.2398419843320026×10⁻⁶ [V⋅m] SI2019

julia> planck(British) # ft⋅lb⋅s 𝘩⋅g₀⁻¹ft⁻¹lb⁻¹ = 4.887138541095932×10⁻³⁴ [lb⋅ft⋅s] British ```
