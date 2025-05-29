```
Phong(;τ = 0.0, ρd = 0.0, ρsmax = 0.0, n = 2)
```

Create a `Phong` material object from the values of transmittance (`τ`) diffuse reflectance (`ρd`), maximum Phong specular reflectance (`ρsmax`) and `n` is the specular exponent that controls the "Phong reflectance lobe". When more than one wavelength is being simulated, a tuple of values should be passed for each optical property (as in `τ = (0.1, 0.3)`).

## Examples

```jldoctest
julia> p = Phong(τ = 0.1, ρd = 0.2, ρsmax = 0.5);

julia> p = Phong(τ = (0.1, 0.45), ρd = (0.2, 0.45), ρsmax = (0.5, 0.5));
```
