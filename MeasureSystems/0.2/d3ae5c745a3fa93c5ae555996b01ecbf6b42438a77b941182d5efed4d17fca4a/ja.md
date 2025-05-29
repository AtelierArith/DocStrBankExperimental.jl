```Julia
jupiterdistance(U::UnitSystem) = length(𝟏,U,IAUJ)
length : [L], [L], [L], [L], [L]
L⋅259493 [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

```

太陽と惑星ジュピターの標準距離 (m または ft)。

```Julia
julia> jupiterdistance(Metric) # m
2⁶3⋅5⁶⋅259493 = 7.78479×10¹¹ [m] メトリック

julia> jupiterdistance(IAU) # au
au⁻¹2⁶3⋅5⁶⋅259493 = 5.20381069836(10) [au] IAU☉

julia> jupiterdistance(Metric)/lightspeed(Metric) # s
𝘤⁻¹2⁶3⋅5⁶⋅259493 = 2596.726432657622 [s] メトリック
```
