```Julia
Engineering = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,Rᵤ,g₀)
F=F, M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=A, R=𝟙, C=𝟙
```

標準メトリック `Engineering` システムは、キログラムとキロポンド（キログラム重）単位に基づいています。

```Julia
julia> boltzmann(Engineering) # kgf⋅m⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹g₀⁻¹2⁴5³ = 1.40787016925(43) × 10⁻²⁴ [kgf⋅m⋅K⁻¹] Engineering

julia> planckreduced(Engineering) # kgf⋅m⋅s⋅rad⁻¹
𝘩⋅g₀⁻¹τ⁻¹ = 1.0753639802033891×10⁻³⁵ [kgf⋅m⋅s⋅rad⁻¹] Engineering

julia> lightspeed(Engineering) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] Engineering

julia> vacuumpermeability(Engineering) # kgf⋅s²⋅C⁻²
g₀⁻¹τ⋅2⁻⁶5⁻⁷ = 1.2814131853751459×10⁻⁷ [kgf⋅s²C⁻²] Engineering

julia> electronmass(Engineering) # kg
𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg] Engineering

julia> molarmass(Engineering) # kg⋅mol⁻¹
2⁻³5⁻³ = 0.001 [kg⋅mol⁻¹] Engineering

julia> luminousefficacy(Engineering) # lm⋅s⋅m⁻¹⋅kgf⁻¹
Kcd⋅g₀ = 6698.135043821981 [kgf⁻¹m⁻¹s⋅lm] Engineering

julia> gravity(Engineering) # kg⋅m⋅kgf⁻¹⋅s⁻²
g₀ = 9.80665 [kgf⁻¹kg⋅m⋅s⁻²] Engineering
```
