```Julia
SI2019 = MetricSystem(Mᵤ,μ₀)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

近似`molarmass`と`vacuumpermeability`に基づく国際単位系。

```Julia
julia> boltzmann(SI2019) # J⋅K⁻¹
kB = 1.380649×10⁻²³ [J⋅K⁻¹] SI2019

julia> planckreduced(SI2019) # J⋅s⋅rad⁻¹
𝘩⋅τ⁻¹ = 1.0545718176461565×10⁻³⁴ [J⋅s] SI2019

julia> lightspeed(SI2019) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] SI2019

julia> vacuumpermeability(SI2019) # H⋅m⁻¹
𝘩⋅𝘤⁻¹𝘦⁻²α⋅2 = 1.25663706212(19) × 10⁻⁶ [H⋅m⁻¹] SI2019

julia> electronmass(SI2019) # kg
𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg] SI2019

julia> molarmass(SI2019) # kg⋅mol⁻¹
NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2 = 0.00099999999966(31) [kg⋅mol⁻¹] SI2019

julia> luminousefficacy(SI2019) # lm⋅W⁻¹
Kcd = 683.01969009009 [lm⋅W⁻¹] SI2019
```
