```Julia
CODATA = ConventionalSystem(RK2014,KJ2014,Rᵤ2014)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

国際科学評議会のデータ委員会に基づく`UnitSystem`の参照。

```Julia
julia> josephson(CODATA) # Hz⋅V⁻¹
KJ = 4.835978525(30) × 10¹⁴ [Hz⋅V⁻¹] CODATA

julia> klitzing(CODATA) # Ω
RK = 25812.8074555(59) [Ω] CODATA

julia> boltzmann(CODATA) # J⋅K⁻¹
𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹RK⁻¹KJ⁻²Rᵤ2014⋅2⁶5³ = 1.38064851(80) × 10⁻²³ [J⋅K⁻¹] CODATA

julia> planckreduced(CODATA) # J⋅s⋅rad⁻¹
RK⁻¹KJ⁻²τ⁻¹2² = 1.054571800(13) × 10⁻³⁴ [J⋅s] CODATA

julia> lightspeed(CODATA) # m⋅s⁻¹
𝘃 = 2.99792458×10⁸ [m⋅s⁻¹] CODATA

julia> vacuumpermeability(CODATA) # H⋅m⁻¹
𝘤⁻¹α⋅RK⋅2 = 1.25663706194(35) × 10⁻⁶ [H⋅m⁻¹] CODATA

julia> electronmass(CODATA) # kg
𝘤⁻¹R∞⋅α⁻²RK⁻¹KJ⁻²2³ = 9.10938355(11) × 10⁻³¹ [kg] CODATA

julia> molarmass(CODATA) # kg⋅mol⁻¹
2⁻³5⁻³ = 0.001 [kg⋅mol⁻¹] CODATA

julia> luminousefficacy(CODATA) # lm⋅W⁻¹
𝘩⋅Kcd⋅RK⋅KJ²2⁻² = 683.0197015(85) [lm⋅W⁻¹] CODATA
```
