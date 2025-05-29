```
chirp(f, b, ω₀=photon_energy(f))
```

Returns the field resulting from applying a [`Chirp`](@ref) to the field `f`.

# Example

```julia
julia> @field(F) do
           I₀ = 1.0
           T = 2.0u"fs"
           σ = 3.0
           Tmax = 3.0
       end
Linearly polarized field with
  - I₀ = 1.0000e+00 au = 3.5094452e16 W cm⁻² =>
    - E₀ = 1.0000e+00 au = 514.2207 GV m⁻¹
    - A₀ = 13.1594 au
  – a Fixed carrier @ λ = 599.5849 nm (T = 2.0000 fs, ω = 0.0760 Ha = 2.0678 eV, f = 500.0000 THz)
  – and a Gaussian envelope of duration 170.8811 as (intensity FWHM; ±82.68σ)
  – and a bandwidth of 0.3925 Ha = 10.6797 eV ⟺ 2.5823 PHz ⟺ 58518.2144 Bohr = 3.0967 μm
  – Uₚ = 43.2922 Ha = 1.1780 keV => α = 173.1690 Bohr = 9.1637 nm

julia> chirp(F, austrip(1u"fs^2"))
DispersedField:
Linearly polarized field with
  - I₀ = 1.0000e+00 au = 3.5094452e16 W cm⁻² =>
    - E₀ = 1.0000e+00 au = 514.2207 GV m⁻¹
    - A₀ = 13.1594 au
  – a Fixed carrier @ λ = 599.5849 nm (T = 2.0000 fs, ω = 0.0760 Ha = 2.0678 eV, f = 500.0000 THz)
  – and a Gaussian envelope of duration 170.8811 as (intensity FWHM; ±82.68σ)
  – and a bandwidth of 0.3925 Ha = 10.6797 eV ⟺ 2.5823 PHz ⟺ 58518.2144 Bohr = 3.0967 μm
  – Uₚ = 43.2922 Ha = 1.1780 keV => α = 173.1690 Bohr = 9.1637 nm
  – dispersed through Chirp(b = 1709.1091 = 1.0000 fs², ω₀ = 0.0760 = 2.0678 eV)
```
