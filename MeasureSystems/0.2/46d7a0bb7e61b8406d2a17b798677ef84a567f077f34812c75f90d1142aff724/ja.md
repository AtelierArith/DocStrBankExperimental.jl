```Julia
エタンドル : [L²A²], [L²], [L²], [L²], [L²]
etendue(U::UnitSystem,S::UnitSystem) = area(U,S)*solidangle(U,S)
etendue(v::Real,U::UnitSystem,S::UnitSystem) = v/etendue(U,S)
L²A² [ħ²𝘤⁻²mₑ⁻²ϕ⁴g₀²] 統一

エタンドルまたは `area` と `solidangle` の積 (m², ft²)、単位換算係数。

```

Julia julia> etendue(CGS,Metric) # m²⋅cm⁻² 2⁻⁴5⁻⁴ = 0.0001 [m²]/[cm²] ガウス -> メトリック

julia> etendue(English,Metric) # m²⋅ft⁻² ft² = 0.09290304 [m²]/[ft²] 英語 -> メトリック ```
