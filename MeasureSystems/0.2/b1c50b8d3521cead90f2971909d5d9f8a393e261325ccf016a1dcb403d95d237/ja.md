```Julia
MPH = EntropySystem(FPS,HOUR,mi,𝟏)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

`FPS` 絶対 `UnitSystem` に基づくマイルポンド時仕様。

```Julia
julia> boltzmann(MPH) # lbf⋅mi²⋅hr⁻²⋅F⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹ft⁻²lb⁻¹2²5⁶11⁻² = 8.4615956484(26) × 10⁻²³ [lb⋅mi²h⁻²°R⁻¹] MPH

julia> planckreduced(MPH) # lbf⋅mi²⋅hr⁻¹⋅rad⁻¹
𝘩⋅ft⁻²lb⁻¹τ⁻¹2⁻⁶11⁻² = 3.2315817800735083×10⁻³⁷ [lb⋅mi²h⁻¹] MPH

julia> lightspeed(MPH) # mi⋅hr⁻¹
𝘤⋅ft⁻¹2⁻¹3⋅5⋅11⁻¹ = 6.706166293843951×10⁸ [mi⋅h⁻¹] MPH

julia> vacuumpermeability(MPH) # lbm⋅mi⋅C⁻²
ft⁻¹lb⁻¹τ⋅2⁻¹¹3⁻¹5⁻⁸11⁻¹ = 1.7214532710813804×10⁻⁹ [lb⋅mi⋅C⁻²] MPH

julia> electronmass(MPH) # lbm
𝘩⋅𝘤⁻¹R∞⋅α⁻²lb⁻¹2 = 2.00827533796(62) × 10⁻³⁰ [lb] MPH

julia> molarmass(MPH) # lbm⋅lb-mol⁻¹
𝟏 = 1.0 [lb⋅lb-mol⁻¹] MPH

julia> luminousefficacy(MPH) # lm⋅h³⋅lb⁻¹⋅mi⁻²
Kcd⋅ft²lb⋅2⁻²3⁻⁴5⁻⁴11² = 0.017198446999173198 [lb⁻¹mi⁻²h³lm] MPH
```
