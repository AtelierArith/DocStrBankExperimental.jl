```Julia
molarsusceptibility : [L³N⁻¹A⁻¹R⁻¹], [L³N⁻¹], [L³N⁻¹], [L³N⁻¹], [L³N⁻¹]
molarsusceptibility(U::UnitSystem,S::UnitSystem) = specificsusceptibility(U,S)*molarmass(U,S)
molarsusceptibility(v::Real,U::UnitSystem,S::UnitSystem) = v/molarsusceptibility(U,S)
L³N⁻¹A⁻¹R⁻¹ [ħ³𝘤⁻³mₑ⁻⁴Mᵤ⋅ϕ²λ⁻¹g₀³] 統一

磁気/電気モル質量 `susceptibility` (m³⋅mol⁻¹)、単位換算係数。

```

Julia julia> molarsusceptibility(CGS,Metric) # m³⋅cm⁻³ τ⋅2⁻⁵5⁻⁶ = 1.2566370614359172×10⁻⁵ [m³]/[mL] ガウス -> メトリック

julia> molarsusceptibility(Metric,SI2019) # m³⋅mol⋅mol⁻¹⋅cm⁻³ NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 0.99999999966(31) [mol⁻¹]/[mol⁻¹] メトリック -> SI2019 ```
