```Julia
horsepowerwatt(U::UnitSystem) = power(𝟐^4*𝟑^3/𝟓*τ,U,British)
```

Unit of `power` derived from Watt's exact original horse power estimate.

```Julia
julia> horsepowerwatt(British) # lb⋅ft⋅s⁻¹
542.8672105403163

julia> horsepowerwatt(Metric) # W
736.0291076111621

julia> horsepowerwatt(Engineering) # kgf⋅m⋅s⁻¹
75.05408142547783
```
