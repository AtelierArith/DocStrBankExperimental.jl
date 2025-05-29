```Julia
輝度 : [L⁻²JA⁻²], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
luminance(U::UnitSystem,S::UnitSystem) = luminousintensity(U,S)/area(U,S)
luminance(v::Real,U::UnitSystem,S::UnitSystem) = v/luminance(U,S)
L⁻²JA⁻² [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻⁵g₀⁻⁴] 統一

```

面積あたりの光度または輝度 (cd⋅m⁻², lm⋅m⁻²⋅rad⁻²)、単位変換係数。

```Julia
julia> luminance(CGS,Metric) # lx⋅ph⁻¹
2⁴5⁴ = 10000.0 [m⁻²]/[cm⁻²] ガウス -> メトリック

julia> luminance(IAU,Metric) # lx⋅au²⋅lm⁻¹
au⁻² = 4.46837049952(18) × 10⁻²³ [m⁻²]/[au⁻²] IAU☉ -> メトリック

julia> luminance(English,Metric) # ft²⋅m⁻²
ft⁻² = 10.76391041670972 [m⁻²]/[ft⁻²] 英語 -> メトリック

julia> 1/10.76 # lx⋅fc⁻¹
0.0929368029739777
```
