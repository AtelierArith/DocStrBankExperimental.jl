```Julia
照度 : [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
照度(U::UnitSystem,S::UnitSystem) = 光束(U,S)/面積(U,S)
照度(v::Real,U::UnitSystem,S::UnitSystem) = v/照度(U,S)
L⁻²J [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻³g₀⁻⁴] 統一

```

面積あたりの光束または輝度 (lx, lm⋅m⁻², cd⋅m⁻²⋅rad²)、単位換算係数。

```Julia
julia> 照度(CGS,Metric) # lx⋅ph⁻¹
2⁴5⁴ = 10000.0 [m⁻²]/[cm⁻²] ガウス -> メトリック

julia> 照度(IAU,Metric) # lx⋅au²⋅lm⁻¹
au⁻² = 4.46837049952(18) × 10⁻²³ [m⁻²]/[au⁻²] IAU☉ -> メトリック

julia> 照度(English,Metric) # ft²⋅m⁻²
ft⁻² = 10.76391041670972 [m⁻²]/[ft⁻²] 英語 -> メトリック

julia> 1/10.76 # lx⋅fc⁻¹
0.0929368029739777
```
