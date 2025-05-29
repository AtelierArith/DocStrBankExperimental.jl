```Julia
Engineering = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,Rᵤ,g₀)
```

キログラムとキロポンド（キログラム重）単位に基づく標準メトリック `Engineering` システム。

```Julia
julia> boltzmann(Engineering) # kgf⋅m⋅K⁻¹
1.4078701692478171e-24

julia> planckreduced(Engineering) # kgf⋅m⋅s⋅rad⁻¹
1.0753639802033891e-35

julia> lightspeed(Engineering) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(Engineering) # kgf⋅s²⋅C⁻²
1.2814131853751459e-7

julia> electronmass(Engineering) # kg
9.109383701558256e-31

julia> molarmass(Engineering) # kg⋅mol⁻¹
0.001

julia> luminousefficacy(Engineering) # lm⋅s⋅m⁻¹⋅kgf⁻¹
6698.135043821981

julia> gravity(Engineering) # kg⋅m⋅kgf⁻¹⋅s⁻²
9.80665
```
