```Julia
Nautical = EntropySystem(Metric,HOUR,nm,em^3,𝟏,τ*𝟑^3/𝟐^10/𝟓^12,milli)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

海里、キロ地球グラム、`Meridian` 定義に基づく時間の仕様。

```Julia
julia> greatcircle(Nautical) # nm
2⁵3³5² = 21600.0 [nm] Nautical

julia> boltzmann(Nautical) # keg⋅nm²⋅hr⁻²⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹g₀⁵ᐟ²GME⁻⁵ᐟ²τ⁻⁵2⁴⁹3¹⁰5³² = 5.180046618(26) × 10⁻²³ [keg⋅nm²h⁻²K⁻¹] Nautical

julia> planckreduced(Nautical) # keg⋅nm²⋅hr⁻¹⋅rad⁻¹
𝘩⋅g₀⁵ᐟ²GME⁻⁵ᐟ²τ⁻⁶2⁴¹3⁸5²⁷ = 1.0990666907(55) × 10⁻³⁷ [keg⋅nm²h⁻¹] Nautical

julia> lightspeed(Nautical) # nm⋅hr⁻¹
𝘤⋅g₀¹ᐟ²GME⁻¹ᐟ²τ⁻¹2⁹3⁵5⁴ = 5.8195383759(58) × 10⁸ [nm⋅h⁻¹] Nautical

julia> vacuumpermeability(Nautical) # keg⋅nm⋅eC⁻²
τ⋅2⁻¹⁰3³5⁻¹² = 6.785840131753953×10⁻¹⁰ [keg⋅nm⋅eC⁻²] Nautical

julia> electronmass(Nautical) # keg
𝘩⋅𝘤⁻¹R∞⋅α⁻²g₀³ᐟ²GME⁻³ᐟ²τ⁻³2²⁸5²¹ = 9.069925385(27) × 10⁻³¹ [keg] Nautical

julia> molarmass(Nautical) # keg⋅eg-mol⁻¹
2⁻³5⁻³ = 0.001 [keg⋅eg-mol⁻¹] Nautical

julia> luminousefficacy(Nautical) # lm⋅h³⋅keg⁻¹⋅nm⁻²
Kcd⋅g₀⁻⁵ᐟ²GME⁵ᐟ²τ⁵2⁻⁴⁹3⁻¹²5⁻³¹ = 0.05056853095(25) [keg⁻¹nm⁻²h³lm] Nautical
```
