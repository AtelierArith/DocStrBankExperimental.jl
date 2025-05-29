```
GaussianBeam(w0=100e-6, z=0.0, n=1.0, λ=633e-9, zpos=0.0)
```

Defines a physical Gaussian beam. All parameters can be defined with keywords.

Beam initial width `w0`, propagation distance `z`, refractive index `n`  and vacuum wavelength `λ`. `zpos` defines a global position which is not used to calculate the q parameter but instead is for tracking purposes

See also [`GeometricBeamBeam`](@ref).

## Example

```jldoctest
julia> GaussianBeam(w0=100e-6, z=12.0, n=1.0, λ=633e-9, zpos=0.0)
GaussianBeam{Float64}(12.0 + 0.049630215696521214im, 0.0, 1.0, 6.33e-7)
```
