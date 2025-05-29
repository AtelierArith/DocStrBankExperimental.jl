```
WindowedField(field, a, b)
```

Wrapper around any electric `field`, windowed such that it is zero outside the time interval `a..b`.

# Example

```jldoctest
julia> @field(A) do
           I₀ = 1.0
           T = 2.0
           σ = 3.0
           Tmax = 3.0
       end
Linearly polarized field with
  - I₀ = 1.0000e+00 au = 3.5094452e16 W cm^-2 =>
    - E₀ = 1.0000e+00 au = 514.2207 GV m^-1
    - A₀ = 0.3183 au
  – a Fixed carrier @ λ = 14.5033 nm (T = 48.3777 as, ω = 3.1416 Ha = 85.4871 eV, f = 20.6707 PHz)
  – and a Gaussian envelope of duration 170.8811 as (intensity FWHM; ±2.00σ)
  – and a bandwidth of 0.3925 Ha = 10.6797 eV ⟺ 2.5823 PHz ⟺ 34.2390 Bohr = 1.8119 nm
  – Uₚ = 0.0253 Ha = 689.2724 meV => α = 0.1013 Bohr = 5.3617 pm

julia> B = WindowedField(A, -3, 5)
Window from -3.0000 jiffies = -72.5665 as to 5.0000 jiffies = 120.9442 as of
Linearly polarized field with
  - I₀ = 1.0000e+00 au = 3.5094452e16 W cm^-2 =>
    - E₀ = 1.0000e+00 au = 514.2207 GV m^-1
    - A₀ = 0.3183 au
  – a Fixed carrier @ λ = 14.5033 nm (T = 48.3777 as, ω = 3.1416 Ha = 85.4871 eV, f = 20.6707 PHz)
  – and a Gaussian envelope of duration 170.8811 as (intensity FWHM; ±2.00σ)
  – and a bandwidth of 0.3925 Ha = 10.6797 eV ⟺ 2.5823 PHz ⟺ 34.2390 Bohr = 1.8119 nm
  – Uₚ = 0.0253 Ha = 689.2724 meV => α = 0.1013 Bohr = 5.3617 pm

julia> span(A), span(B)
(-6.0 .. 6.0, -3.0 .. 5.0)

julia> field_amplitude(A, -4)
-0.6395632362683398

julia> field_amplitude(B, -4)
0.0
```
