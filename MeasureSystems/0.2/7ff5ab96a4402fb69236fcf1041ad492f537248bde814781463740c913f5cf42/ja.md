```Julia
FPS = RankineSystem(Metric,ft,lb)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

フィート、ポンド、秒、およびポンダルに基づく絶対英語 `UnitSystem`。

```Julia
julia> boltzmann(FPS) # ft⋅pdl⋅°R⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹ft⁻²lb⁻¹2⁴3⁻²5⁴ = 1.82018324169(56) × 10⁻²² [lb⋅ft²s⁻²°R⁻¹] FPS

julia> planckreduced(FPS) # ft⋅pdl⋅s⋅rad⁻¹
𝘩⋅ft⁻²lb⁻¹τ⁻¹ = 2.5025369304889247×10⁻³³ [lb⋅ft²s⁻¹] FPS

julia> lightspeed(FPS) # ft⋅s⁻¹
𝘤⋅ft⁻¹ = 9.835710564304461×10⁸ [ft⋅s⁻¹] FPS

julia> vacuumpermeability(FPS) # lb⋅ft⋅C⁻²
ft⁻¹lb⁻¹τ⋅2⁻⁶5⁻⁷ = 9.089273271309687×10⁻⁶ [lb⋅ft⋅C⁻²] FPS

julia> electronmass(FPS) # lb
𝘩⋅𝘤⁻¹R∞⋅α⁻²lb⁻¹2 = 2.00827533796(62) × 10⁻³⁰ [lb] FPS

julia> molarmass(FPS) # lb⋅lb-mol⁻¹
𝟏 = 1.0 [lb⋅lb-mol⁻¹] FPS

julia> luminousefficacy(FPS) # lm⋅s³⋅lb⁻¹⋅ft⁻²
Kcd⋅ft²lb = 28.78252493663283 [lb⁻¹ft⁻²s³lm] FPS
```
