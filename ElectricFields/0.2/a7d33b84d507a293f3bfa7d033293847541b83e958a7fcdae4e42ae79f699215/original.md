```
dimensions(f)
```

Return the number of dimensions of the field `f`. See also [`polarization`](@ref).

# Examples

```jldoctest
julia> @field(F) do
           I₀ = 2.0
           T = 2.0
           σ = 3.0
           Tmax = 3.0
       end
Linearly polarized field with
  - I₀ = 2.0000e+00 au = 7.0188904e16 W cm^-2 =>
    - E₀ = 1.4142e+00 au = 727.2178 GV m^-1
    - A₀ = 0.4502 au
  – a Fixed carrier @ λ = 14.5033 nm (T = 48.3777 as, ω = 3.1416 Ha = 85.4871 eV, f = 20.6707 PHz)
  – and a Gaussian envelope of duration 170.8811 as (intensity FWHM; ±2.00σ)
  – and a bandwidth of 0.3925 Ha = 10.6797 eV ⟺ 2.5823 PHz ⟺ 34.2390 Bohr = 1.8119 nm
  – Uₚ = 0.0507 Ha = 1.3785 eV => α = 0.1433 Bohr = 7.5826 pm

julia> dimensions(F)
1

julia> @field(F) do
           I₀ = 2.0
           T = 2.0
           σ = 3.0
           Tmax = 3.0
           ξ = 1.0
       end
Transversely polarized field with
  - I₀ = 2.0000e+00 au = 7.0188904e16 W cm^-2 =>
    - E₀ = 1.4142e+00 au = 727.2178 GV m^-1
    - A₀ = 0.4502 au
  – a Elliptical carrier with ξ = 1.00 (RCP) @ λ = 14.5033 nm (T = 48.3777 as, ω = 3.1416 Ha = 85.4871 eV, f = 20.6707 PHz)
  – and a Gaussian envelope of duration 170.8811 as (intensity FWHM; ±2.00σ)
  – and a bandwidth of 0.3925 Ha = 10.6797 eV ⟺ 2.5823 PHz ⟺ 34.2390 Bohr = 1.8119 nm
  – Uₚ = 0.0507 Ha = 1.3785 eV => α = 0.1433 Bohr = 7.5826 pm

julia> dimensions(F)
3
```
