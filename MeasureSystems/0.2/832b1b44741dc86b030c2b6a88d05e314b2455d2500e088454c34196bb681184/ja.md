```Julia
angstrom(U::UnitSystem) = hecto*pico*meter(U)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²τ⋅2⁻⁹5⁻¹⁰ = 258.960507484(79)) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

Metric unit of `length` (m or ft).

```

Julia julia> angstrom(CGS) # cm 2⁻⁸5⁻⁸ = 1.0×10⁻⁸ [cm] ガウス

julia> angstrom(English) # ft ft⁻¹2⁻¹⁰5⁻¹⁰ = 3.280839895013123×10⁻¹⁰ [ft] 英語

julia> angstrom(IPS) # in ft⁻¹2⁻⁸3⋅5⁻¹⁰ = 3.937007874015747×10⁻⁹ [in] IPS ```
