```Julia
conductancequantum(U::UnitSystem) = 𝟐*elementarycharge(U)^2/planck(U) # 2/klitzing(U)
conductance : [F⁻¹L⁻¹T⁻¹Q²], [F⁻¹L⁻¹T⁻¹Q²], [M⁻¹L⁻²TQ²], [L⁻¹T], [LT⁻¹]
F⁻¹L⁻¹T⁻¹Q²⋅(α⋅2² = 0.0291894102771(45)) [𝘤⁻¹μ₀⁻¹λ⁻¹αL⁻²] 統一

```

導電量 `G₀` は、電気伝導度 (S) の量子化された単位です。

```Julia
julia> conductancequantum(SI2019) # S
𝘩⁻¹𝘦²2 = 7.748091729863649×10⁻⁵ [S] SI2019

julia> conductancequantum(Metric) # S
𝘤⁻¹α⋅τ⁻¹2⁸5⁷ = 7.7480917341(12) × 10⁻⁵ [S] Metric

julia> conductancequantum(Conventional) # S
RK90⁻¹2 = 7.74809186773062×10⁻⁵ [S] Conventional

julia> conductancequantum(CODATA) # S
RK⁻¹2 = 7.7480917310(18) × 10⁻⁵ [S] CODATA

julia> conductancequantum(International) # S
𝘤⁻¹α⋅Ωᵢₜ⋅τ⁻¹2⁸5⁷ = 7.7519270395(12) × 10⁻⁵ [S] International

julia> conductancequantum(InternationalMean) # S
𝘤⁻¹α⋅τ⁻¹2⁸5⁷⋅1.00049 = 7.7518882990(12) × 10⁻⁵ [S] InternationalMean

julia> conductancequantum(EMU) # abS
𝘤⁻¹α⋅τ⁻¹2⁻¹5⁻² = 7.7480917341(12) × 10⁻¹⁴ [cm⁻¹s] EMU

julia> conductancequantum(ESU) # statS
𝘤⋅α⋅τ⁻¹2³5² = 6.9636375713(11) × 10⁷ [cm⋅s⁻¹] ESU
```
