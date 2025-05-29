```Julia
Meridian = EntropySystem(Metric,𝟏,em,em^3,𝟏,τ/𝟐^6/𝟓^7,milli)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

フランスの元の `earthmeter` 定義によって定義された現代の理想的な `Meridian` システム。

```Julia
julia> greatcircle(Meridian) # em
2⁹5⁷ = 4.0×10⁷ [em] Meridian

julia> boltzmann(Meridian) # eJ⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹g₀⁵ᐟ²GME⁻⁵ᐟ²τ⁻⁵2⁴⁹5³⁸ = 1.3706960050(69) × 10⁻²³ [eJ⋅K⁻¹] Meridian

julia> planckreduced(Meridian) # eJ⋅s⋅rad⁻¹
𝘩⋅g₀⁵ᐟ²GME⁻⁵ᐟ²τ⁻⁶2⁴⁵5³⁵ = 1.0469694890(53) × 10⁻³⁴ [eJ⋅s] Meridian

julia> lightspeed(Meridian) # em⋅s⁻¹
𝘤⋅g₀¹ᐟ²GME⁻¹ᐟ²τ⁻¹2⁹5⁷ = 2.9935896996(3) × 10⁸ [em⋅s⁻¹] Meridian

julia> vacuumpermeability(Meridian) # kegf⋅s²⋅eC⁻²
τ⋅2⁻⁶5⁻⁷ = 1.2566370614359173×10⁻⁶ [eH⋅em⁻¹] Meridian

julia> electronmass(Meridian) # keg
𝘩⋅𝘤⁻¹R∞⋅α⁻²g₀³ᐟ²GME⁻³ᐟ²τ⁻³2²⁸5²¹ = 9.069925385(27) × 10⁻³¹ [keg] Meridian

julia> molarmass(Meridian) # keg⋅eg-mol⁻¹
2⁻³5⁻³ = 0.001 [keg⋅eg-mol⁻¹] Meridian

julia> luminousefficacy(Meridian) # lm⋅W⁻¹
Kcd⋅g₀⁻⁵ᐟ²GME⁵ᐟ²τ⁵2⁻⁴⁵5⁻³⁵ = 687.9792808(35) [lm⋅eW⁻¹] Meridian
```
