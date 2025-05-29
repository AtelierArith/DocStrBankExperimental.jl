```Julia
liter(U::UnitSystem) = volume(𝟏𝟎^-3,U,Metric)
volume : [L³], [L³], [L³], [L³], [L³]
L³⋅(R∞³α⁻⁶τ³5⁻³ = 1.7366032619(16) × 10³⁴) [ħ³𝘤⁻³mₑ⁻³ϕ³g₀³] 統一

```

`volume`の単位は1立方デシメートル（m³またはft³）から導出されます。

```Julia
julia> liter(Metric) # m³
2⁻³5⁻³ = 0.001 [m³] メトリック

julia> liter(CGS) # cm³
2³5³ = 1000.0 [mL] ガウス

julia> liter(IPS) # in³
ft⁻³2³3³5⁻³ = 61.02374409473227 [in³] IPS
```
