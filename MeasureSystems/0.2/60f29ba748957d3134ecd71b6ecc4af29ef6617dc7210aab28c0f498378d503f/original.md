```Julia
rydberg(U::UnitSystem) = hartree(U)/2planck(U)/lightspeed(U) # Eₕ/2𝘩/𝘤
wavenumber : [L⁻¹], [L⁻¹], [L⁻¹], [L⁻¹], [L⁻¹]
L⁻¹⋅(α²τ⁻¹2⁻¹ = 4.2376081491(13) × 10⁻⁶) [ħ⁻¹𝘤⋅mₑ⋅ϕ⁻¹g₀⁻¹] Unified
```

Rydberg constant `R∞` is lowest energy photon capable of ionizing atom at ground state (m⁻¹).

```Julia
julia> rydberg(Metric) # m⁻¹
R∞ = 1.0973731568160(21) × 10⁷ [m⁻¹] Metric
```

The Rydberg constant for hydrogen `RH` is `R∞*mₚ/(mₑ+mₚ)` (m⁻¹).

```Julia
julia> rydberg(Metric)*protonmass(Metric)/(electronmass(Metric)+protonmass(Metric)) # m⁻¹
𝘩⋅𝘤⁻¹R∞²α⁻²μₑᵤ⁻¹μₚᵤ⋅2⋅5.9753831112(19) × 10²⁶ = 1.09677583403(48) × 10⁷ [m⁻¹] Metric
```

Rydberg unit of photon energy `Ry` is `𝘩*𝘤*R∞` or `Eₕ/2` (J).

```Julia
julia> hartree(Metric)/2 # J
𝘩⋅𝘤⋅R∞ = 2.1798723611036(42) × 10⁻¹⁸ [J] Metric

julia> hartree(SI2019)/𝟐/elementarycharge(SI2019) # eV
𝘩⋅𝘤⋅𝘦⁻¹R∞ = 13.605693122994(26) [V] SI2019
```

Rydberg photon frequency `𝘤*R∞` or `Eₕ/2𝘩` (Hz).

```Julia
julia> lightspeed(Metric)*rydberg(Metric) # Hz
𝘤⋅R∞ = 3.2898419602509(63) × 10¹⁵ [Hz] Metric
```

Rydberg wavelength `1/R∞` (m).

```Julia
julia> 𝟏/rydberg(Metric) # m
R∞⁻¹ = 9.112670505824(17) × 10⁻⁸ [m] Metric

julia> 𝟏/rydberg(Metric)/τ # m⋅rad⁻¹
R∞⁻¹τ⁻¹ = 1.4503265557696(28) × 10⁻⁸ [m] Metric
```

Precision measurements of the Rydberg constants are within a relative standard uncertainty of under 2 parts in 10¹², and is chosen to constrain values of other physical constants.
