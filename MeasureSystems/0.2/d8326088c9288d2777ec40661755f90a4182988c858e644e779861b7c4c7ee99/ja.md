```Julia
jupitermass(U::UnitSystem) = mass(𝘩⁻¹𝘤⁻¹mP²GMJ⋅τ = 1.898124(42) × 10²⁷,U)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻²R∞⁻¹α²mP²GMJ⋅τ⋅2⁻¹ = 2.083702(46) × 10⁵⁷) [mₑ] 統一

Jupiter `mass` の推定値は重力定数の推定値から得られます (kg または slug)。

```

Julia julia> jupitermass(Metric) # kg 𝘩⁻¹𝘤⁻¹mP²GMJ⋅τ = 1.898124(42) × 10²⁷ [kg] メトリック

julia> jupitermass(British) # slug 𝘩⁻¹𝘤⁻¹g₀⁻¹ft⋅lb⁻¹mP²GMJ⋅τ = 1.300628(29) × 10²⁶ [slug] ブリティッシュ

julia> jupitermass(English) # lb 𝘩⁻¹𝘤⁻¹lb⁻¹mP²GMJ⋅τ = 4.184647(92) × 10²⁷ [lbm] イングリッシュ

julia> jupitermass(IAU) # M☉ au⁻³kG⁻²GMJ⋅τ⁻²2²⁸3¹⁴5¹⁰ = 0.000954594262(68) [M☉] IAU☉

julia> jupitermass(IAUE) # ME GME⁻¹GMJ = 317.828383(23) [ME] IAUE

julia> jupitermass(QCD) # mₚ 𝘩⁻²R∞⁻¹α²μₑᵤ⋅μₚᵤ⁻¹mP²GMJ⋅τ⋅2⁻¹ = 1.134820(25) × 10⁵⁴ [mₚ] QCD

julia> jupitermass(Metric)/dalton(Metric) # Da 𝘩⁻²R∞⁻¹α²μₑᵤ⋅mP²GMJ⋅τ⋅2⁻¹ = 1.143077(25) × 10⁵⁴ [𝟙] メトリック ```
