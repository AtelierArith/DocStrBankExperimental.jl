```Julia
einstein(U::UnitSystem) = 𝟐^2*τ*gravitation(U)/lightspeed(U)^4
```

アインシュタインの場の方程式からの重力定数 (s⋅²⋅m⁻¹⋅kg⁻¹)。

```Julia
julia> einstein(Metric) # s²⋅m⁻¹⋅kg⁻¹
2.0766480968545148e-43

julia> einstein(IAU) # day²⋅au⁻¹⋅M☉⁻¹
8.274973467748227e-12
```
