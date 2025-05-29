```Julia
FFF = EntropySystem(Metric,𝟐*𝟕*DAY,fur,𝟐*𝟑^2*𝟓*lb,°R,0,𝟏)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

Furlong–firkin–fortnight `FFF` is a humorous `UnitSystem` based on unusal impractical units.

```Julia
julia> boltzmann(FFF) # fir⋅fur²⋅ftn⁻²⋅F⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹ft⁻²lb⁻¹2¹⁵5⁵7²11⁻² = 6.7931043720(21) × 10⁻¹⁸ [fir⋅fur²ftn⁻²°R⁻¹] FFF

julia> planckreduced(FFF) # fir⋅fur²⋅ftn⁻¹⋅rad⁻¹
𝘩⋅ft⁻²lb⁻¹τ⁻¹2³3⁻¹5⁻¹7⋅11⁻² = 7.721326066522302×10⁻³⁵ [fir⋅fur²ftn⁻¹] FFF

julia> lightspeed(FFF) # fur⋅ftn⁻¹
𝘤⋅ft⁻¹2⁶3²5⋅7⋅11⁻¹ = 1.8026174997852542×10¹² [fur⋅ftn⁻¹] FFF

julia> vacuumpermeability(FFF) # fir⋅fur⋅Inf⁻²
𝟏/Inf = 0.0 [fir⋅fur⋅Inf⁻²] FFF

julia> electronmass(FFF) # fir
𝘩⋅𝘤⁻¹R∞⋅α⁻²lb⁻¹3⁻²5⁻¹ = 2.23141704217(68) × 10⁻³² [fir] FFF

julia> molarmass(FFF) # fir⋅fir-mol⁻¹
𝟏 = 1.0 [fir⋅fir-mol⁻¹] FFF

julia> luminousefficacy(FFF) # lm⋅ftn³⋅fir⁻¹⋅fur⁻²
Kcd⋅ft²lb⋅2⁻¹⁹3⁻⁵5⁻³7⁻³11² = 6.375788993269436×10⁻¹⁰ [fir⁻¹fur⁻²ftn³lm] FFF
```
