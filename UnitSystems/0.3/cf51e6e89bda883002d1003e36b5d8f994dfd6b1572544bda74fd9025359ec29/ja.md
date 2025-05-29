```Julia
specificimpedance(U::UnitSystem,S::UnitSystem) = pressure(U,S)/speed(U,S)
specificimpedance(v::Real,U::UnitSystem,S::UnitSystem) = v/specificimpedance(U,S)
```

特性特定音響インピーダンス (Rayl, Pa⋅s⋅m⁻¹)、単位換算係数。

```Julia
julia> specificimpedance(CGS,Metric) # Pa⋅cm⋅m⁻¹⋅Ba⁻¹
9.999999999999996

julia> specificimpedance(English,Metric) # Pa⋅ft³⋅m⁻¹⋅lb⁻¹
157.08746384624618
```
