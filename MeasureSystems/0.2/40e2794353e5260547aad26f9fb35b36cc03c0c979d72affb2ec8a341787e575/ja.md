```Julia
SI1976 = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,8.31432)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

1976年標準大気圧からの普遍気体定数`8.31432`を持つ`UnitSystem`を参照してください。

```Julia
julia> boltzmann(SI1976) # J⋅K⁻¹
𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³⋅8.31432 = 1.38062531722(43) × 10⁻²³ [kg⋅m²s⁻²K⁻¹] SI1976

julia> planckreduced(SI1976) # J⋅s⋅rad⁻¹
𝘩⋅τ⁻¹ = 1.0545718176461565×10⁻³⁴ [kg⋅m²s⁻¹] SI1976

julia> lightspeed(SI1976) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] SI1976

julia> vacuumpermeability(SI1976) # H⋅m⁻¹
τ⋅2⁻⁶5⁻⁷ = 1.2566370614359173×10⁻⁶ [kg⋅m⋅C⁻²] SI1976

julia> electronmass(SI1976) # kg
𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg] SI1976

julia> molarmass(SI1976) # kg⋅mol⁻¹
2⁻³5⁻³ = 0.001 [kg⋅mol⁻¹] SI1976

julia> luminousefficacy(SI1976) # lm⋅W⁻¹
Kcd = 683.01969009009 [kg⁻¹m⁻²s³lm] SI1976
```
