```Julia
electronradius(U::UnitSystem) = finestructure(U)*planckreduced(U)*gravity(U)/electronmass(U)/lightspeed(U)
angularlength : [LA⁻¹], [L], [L], [L], [L]
LA⁻¹⋅(α = 0.0072973525693(11)) [ħ⋅𝘤⁻¹mₑ⁻¹g₀] Unified
```

Classical electron radius or Lorentz radius or Thomson scattering length (m).

```Julia
julia> electronradius(Metric) # m
R∞⁻¹α³τ⁻¹2⁻¹ = 2.8179403262(13) × 10⁻¹⁵ [m] Metric

julia> electronradius(CODATA) # m
R∞⁻¹α³τ⁻¹2⁻¹ = 2.8179403262(13) × 10⁻¹⁵ [m] CODATA

julia> electronradius(Conventional) # m
R∞⁻¹α³τ⁻¹2⁻¹ = 2.8179403262(13) × 10⁻¹⁵ [m] Conventional

julia> electronradius(Hartree) # a₀
α² = 5.3251354520(16) × 10⁻⁵ [a₀] Hartree
```
