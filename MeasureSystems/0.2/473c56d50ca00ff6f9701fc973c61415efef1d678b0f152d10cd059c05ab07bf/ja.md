```Julia
specificsusceptibility : [M⁻¹L³A⁻¹R⁻¹], [F⁻¹L⁴T⁻²], [M⁻¹L³], [M⁻¹L³], [M⁻¹L³]
specificsusceptibility(U::UnitSystem,S::UnitSystem) = susceptibility(U,S)/density(U,S)
specificsusceptibility(v::Real,U::UnitSystem,S::UnitSystem) = v/specificsusceptibility(U,S)
M⁻¹L³A⁻¹R⁻¹ [ħ³𝘤⁻³mₑ⁻⁴ϕ²λ⁻¹g₀³] 統一

磁気/電気質量特定 `susceptibility` (m³⋅kg⁻¹)、単位換算係数。

```

Julia julia> specificsusceptibility(EMU,Metric) # m³⋅g⋅kg⁻¹⋅cm⁻³ τ⋅2⁻²5⁻³ = 0.012566370614359173 [kg⁻¹m³]/[g⁻¹cm³] EMU -> Metric

julia> specificsusceptibility(ESU,Metric) # m³⋅g⋅kg⁻¹⋅cm⁻³ τ⋅2⁻²5⁻³ = 0.012566370614359173 [kg⁻¹m³]/[g⁻¹cm³] ESU -> Metric

julia> specificsusceptibility(Metric,SI2019) # m³⋅kg⋅kg⁻¹⋅m⁻³ 𝟏 = 1.0 [𝟙]/[𝟙] Metric -> SI2019 ```
