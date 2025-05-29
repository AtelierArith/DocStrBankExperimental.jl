```Julia
solarmass(U::UnitSystem) = mass(𝘩⁻¹𝘤⁻¹au³kG²mP²τ³2⁻²⁸3⁻¹⁴5⁻¹⁰ = 1.988409(44) × 10³⁰,U)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻²R∞⁻¹α²au³kG²mP²τ³2⁻²⁹3⁻¹⁴5⁻¹⁰ = 2.182814(48) × 10⁶⁰) [mₑ] Unified
```

太陽の `mass` は重力定数の推定値から算出されます (kg または slug)。

```Julia
julia> solarmass(Metric) # kg
𝘩⁻¹𝘤⁻¹au³kG²mP²τ³2⁻²⁸3⁻¹⁴5⁻¹⁰ = 1.988409(44) × 10³⁰ [kg] Metric

julia> solarmass(British) # slug
𝘩⁻¹𝘤⁻¹g₀⁻¹au³ft⋅lb⁻¹kG²mP²τ³2⁻²⁸3⁻¹⁴5⁻¹⁰ = 1.362493(30) × 10²⁹ [slug] British

julia> solarmass(English) # lb
𝘩⁻¹𝘤⁻¹au³lb⁻¹kG²mP²τ³2⁻²⁸3⁻¹⁴5⁻¹⁰ = 4.383692(97) × 10³⁰ [lbm] English

julia> solarmass(IAUE) # ME
au³kG²GME⁻¹τ²2⁻²⁸3⁻¹⁴5⁻¹⁰ = 332946.04409(67) [ME] IAUE

julia> solarmass(IAUJ) # MJ
au³kG²GMJ⁻¹τ²2⁻²⁸3⁻¹⁴5⁻¹⁰ = 1047.565484(74) [MJ] IAUJ

julia> solarmass(QCD) # mₚ
𝘩⁻²R∞⁻¹α²μₑᵤ⋅μₚᵤ⁻¹au³kG²mP²τ³2⁻²⁹3⁻¹⁴5⁻¹⁰ = 1.188798(26) × 10⁵⁷ [mₚ] QCD

julia> solarmass(Metric)/dalton(Metric) # Da
𝘩⁻²R∞⁻¹α²μₑᵤ⋅au³kG²mP²τ³2⁻²⁹3⁻¹⁴5⁻¹⁰ = 1.197448(26) × 10⁵⁷ [𝟙] Metric
```
