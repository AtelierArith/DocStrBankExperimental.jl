```
@field(name) do ... end
```

Frontend macro for creating an electric field and storing it in the variable `name`.

# Example

```julia
julia> @field(F) do
           I₀ = 2.0
           T = 2.0
           σ = 3.0
           Tmax = 3.0
       end
Linearly polarized field with
  - I₀ = 2.0000e+00 au = 7.0188904e16 W cm⁻² =>
    - E₀ = 1.4142e+00 au = 727.2178 GV m⁻¹
    - A₀ = 0.4502 au
  – a Fixed carrier @ λ = 14.5033 nm (T = 48.3777 as, ω = 3.1416 Ha = 85.4871 eV)
  – and a Gaussian envelope of duration 170.8811 as (intensity FWHM; ±2.00σ)
```
