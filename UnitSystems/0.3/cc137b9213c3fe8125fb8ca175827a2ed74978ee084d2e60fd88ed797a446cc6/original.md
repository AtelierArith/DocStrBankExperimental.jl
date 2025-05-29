```Julia
tonsrefrigeration(U::UnitSystem) = frequency(𝟐*𝟓/𝟑,U,Metric)*thermalunit(U)
```

Unit of `power` derived from melting of 1 short ton of ice in 24 hours.

```Julia
julia> tonsrefrigeration(British) # lb⋅ft⋅s⁻¹
2593.858709996918

julia> tonsrefrigeration(Metric) # W
3516.800194449555

julia> tonsrefrigeration(Engineering) # kgf⋅m⋅s⁻¹
358.6138176084142
```
