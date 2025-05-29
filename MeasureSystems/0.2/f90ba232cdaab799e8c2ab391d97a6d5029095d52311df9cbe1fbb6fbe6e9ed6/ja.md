```Julia
gravityforce : [F⁻¹MLT⁻²], [𝟙], [𝟙], [𝟙], [𝟙]
gravityforce(U::UnitSystem,S::UnitSystem) = acceleration(U,S)/specificforce(U,S)
gravityforce(v::Real,U::UnitSystem,S::UnitSystem) = v/gravityforce(U,S)
F⁻¹MLT⁻² [g₀] 統一

Reference `acceleration` per `specificforce` (𝟏, F⁻¹MLT⁻²), unit conversion factor.

```

Julia julia> gravityforce(Metric,CGS) 𝟏 = 1.0 [s²]/[s²] Metric -> Gauss

julia> gravityforce(Metric,Engineering) g₀ = 9.80665 [kgf⁻¹]/[N⁻¹] Metric -> Engineering

julia> gravityforce(Metric,English) g₀⋅ft⁻¹ = 32.17404855643044 [lbf⁻¹lbm⋅ft]/[s²] Metric -> English ```
