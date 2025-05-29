```Julia
bohr(U::UnitSystem) = planckreduced(U)*gravity(U)/electronmass(U)/lightspeed(U)/finestructure(U)
angularlength : [LA⁻¹], [L], [L], [L], [L]
LA⁻¹⋅(α⁻¹ = 137.035999084(21)) [ħ⋅𝘤⁻¹mₑ⁻¹g₀] 統一

水素原子の基底状態におけるボーア半径 `a₀` (m)。

```

Julia julia> bohr(Metric) # m R∞⁻¹α⋅τ⁻¹2⁻¹ = 5.29177210902(81) × 10⁻¹¹ [m] Metric

julia> bohr(IPS) # in R∞⁻¹α⋅ft⁻¹τ⁻¹2⋅3 = 2.08337484607(32) × 10⁻⁹ [in] IPS

julia> bohr(Hartree) # a₀ 𝟏 = 1.0 [a₀] Hartree ```
