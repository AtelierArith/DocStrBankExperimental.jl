```Julia
permeance : [FLT²Q⁻²R⁻¹C²], [FLT²Q⁻²], [ML²Q⁻²], [L], [L⁻¹T²]
permeance(U::UnitSystem,S::UnitSystem) = 1/reluctance(U,S)
permeance(v::Real,U::UnitSystem,S::UnitSystem) = v/permeance(U,S)
FLT²Q⁻²R⁻¹C² [ħ⋅𝘤⁻¹μ₀⋅mₑ⁻¹ϕ⋅g₀] Unified
```

Magnetic `permeance` or magnetic conductance (H, Mx⋅Gb⁻¹), unit conversion factor.

```Julia
julia> permeance(EMU,Metric) # abH⋅H⁻¹
τ⋅2⁻⁸5⁻⁹ = 1.2566370614359173×10⁻⁸ [F⁻¹]/[gal] EMU -> Metric

julia> permeance(ESU,Metric) # statH⋅H⁻¹
𝘤²τ⋅2⁻⁴5⁻⁵ = 1.129409066758147×10¹³ [F⁻¹]/[cm⁻¹] ESU -> Metric

julia> permeance(Metric,SI2019) # H⋅H⁻¹
𝘩⋅𝘤⁻¹𝘦⁻²α⋅τ⁻¹2⁷5⁷ = 1.00000000055(15) [C⁻²]/[C⁻²] Metric -> SI2019
```
