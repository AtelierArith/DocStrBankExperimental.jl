```Julia
rydberg(U::UnitSystem) = hartree(U)/2planck(U)/lightspeed(U) # Eₕ/2𝘩/𝘤
```

Rydberg constant `R∞` is lowest energy photon capable of ionizing atom at ground state (m⁻¹).

```Julia
julia> rydberg(Metric) # m⁻¹
1.0973731568160104e7
```

The Rydberg constant for hydrogen `RH` is `R∞*mₚ/(mₑ+mₚ)` (m⁻¹).

```Julia
julia> rydberg(Metric)*protonmass(Metric)/(electronmass(Metric)+protonmass(Metric)) # m⁻¹
1.0967758340280434e7
```

Rydberg unit of photon energy `Ry` is `𝘩*𝘤*R∞` or `Eₕ/2` (J).

```Julia
julia> hartree(Metric)/2 # J
2.1798723611036055e-18

julia> hartree(SI2019)/𝟐/elementarycharge(SI2019) # eV
13.605693122994362
```

Rydberg photon frequency `𝘤*R∞` or `Eₕ/2𝘩` (Hz).

```Julia
julia> lightspeed(Metric)*rydberg(Metric) # Hz
3.289841960250912e15
```

Rydberg wavelength `1/R∞` (m).

```Julia
julia> 𝟏/rydberg(Metric) # m
9.112670505823788e-8

julia> 𝟏/rydberg(Metric)/τ # m⋅rad⁻¹
1.4503265557695781e-8
```

Precision measurements of the Rydberg constants are within a relative standard uncertainty of under 2 parts in 10¹², and is chosen to constrain values of other physical constants.
