```Julia
frequency : [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹]
frequency(U::UnitSystem,S::UnitSystem) = 1/time(U,S)
frequency(v::Real,U::UnitSystem,S::UnitSystem) = v/frequency(U,S)
T⁻¹ [ħ⁻¹𝘤²mₑ⋅ϕ⁻¹g₀⁻¹] 統一

時間あたりの発生数 (Hz または s⁻¹)、単位変換係数。

```

Julia julia> frequency(IAU,Metric) day⋅s⁻¹ 2⁻⁷3⁻³5⁻² = 1.1574074074074075×10⁻⁵ [Hz]/[D⁻¹] IAU☉ -> Metric ```
