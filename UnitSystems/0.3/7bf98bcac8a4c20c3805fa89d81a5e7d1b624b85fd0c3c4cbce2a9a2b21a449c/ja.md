```Julia
horsepowerwatt(U::UnitSystem) = power(𝟐^4*𝟑^3/𝟓*τ,U,British)
```

ワットの正確な元の馬力推定から導出された`power`の単位です。

```Julia
julia> horsepowerwatt(British) # lb⋅ft⋅s⁻¹
542.8672105403163

julia> horsepowerwatt(Metric) # W
736.0291076111621

julia> horsepowerwatt(Engineering) # kgf⋅m⋅s⁻¹
75.05408142547783
```
