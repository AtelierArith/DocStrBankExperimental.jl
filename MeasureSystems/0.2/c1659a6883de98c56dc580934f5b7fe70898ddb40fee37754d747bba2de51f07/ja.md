```Julia
KKH = EntropySystem(Metric,HOUR,kilo,𝟏)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

キロメートル・キログラム・時間の `UnitSystem` バリアントの `Metric` システム。

```Julia
julia> boltzmann(KKH) # kg⋅km²⋅h⁻²⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁶3⁴5 = 1.78932110338(55) × 10⁻²² [kg⋅km²h⁻²K⁻¹] KKH

julia> planckreduced(KKH) # kg⋅km²⋅h⁻¹
𝘩⋅τ⁻¹2⁻²3²5⁻⁴ = 3.7964585435261634×10⁻³⁷ [kg⋅km²h⁻¹] KKH

julia> lightspeed(KKH) # km⋅hr⁻¹
𝘤⋅2⋅3²5⁻¹ = 1.0792528488×10⁹ [km⋅h⁻¹] KKH

julia> vacuumpermeability(KKH) # kg⋅km⋅C⁻²
τ⋅2⁻⁹5⁻¹⁰ = 1.2566370614359174×10⁻⁹ [kg⋅km⋅C⁻²] KKH

julia> electronmass(KKH) # kg
𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg] KKH

julia> molarmass(KKH) # kg⋅mol⁻¹
2⁻³5⁻³ = 0.001 [kg⋅mol⁻¹] KKH

julia> luminousefficacy(KKH) # lm⋅h³⋅kg⁻¹⋅km⁻²
Kcd⋅2⁻⁶3⁻⁶ = 0.014639482383618183 [kg⁻¹km⁻²h³lm] KKH
```
