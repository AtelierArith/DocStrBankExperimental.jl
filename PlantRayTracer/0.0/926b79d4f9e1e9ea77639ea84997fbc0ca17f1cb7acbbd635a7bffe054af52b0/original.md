```
Lambertian(;τ = 0.0, ρ = 0.0)
```

Create a `Lambertian` material object from the values of transmittance (`τ`) and reflectance (`ρ`). When more than one wavelength is being simulated, a tuple of values should be passed for each optical property (as in `τ = (0.1,0.2)`).

## Examples

```jldoctest
julia> l = Lambertian(τ = 0.1, ρ = 0.2);

julia> l = Lambertian(τ = (0.1, 0.45), ρ = (0.2, 0.45));
```
