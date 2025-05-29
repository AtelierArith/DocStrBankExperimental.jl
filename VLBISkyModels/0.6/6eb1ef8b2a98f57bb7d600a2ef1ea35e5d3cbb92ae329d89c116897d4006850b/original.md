```
RadialGaussian(σ)
```

Create a profile that is a radial gaussian ring with radius unity and standard deviation `σ`.

## Notes

This is usually couple with a azimuthal profile to create a general ring template

```julia-repl
julia> rad = RadialGaussian(0.1)
julia> azi = AzimuthalUniform()
julia> t = RingTemplate(rad, azi)
```

## Arguments

  * `σ`: The standard deviation for the Gaussian ring.
