```Julia
tonsrefrigeration(U::UnitSystem) = frequency(𝟐*𝟓/𝟑,U,Metric)*thermalunit(U)
```

1短トンの氷を24時間で溶かすことから導出された`power`の単位。

```Julia
julia> tonsrefrigeration(British) # lb⋅ft⋅s⁻¹
2593.858709996918

julia> tonsrefrigeration(Metric) # W
3516.800194449555

julia> tonsrefrigeration(Engineering) # kgf⋅m⋅s⁻¹
358.6138176084142
```
