```
AzimuthalUniform()
AzimuthalUniform{T}()
```

A azimuthal profile that is uniform for all angles.

## Notes

This is usually couple with a radial profile to create a general ring template

```julia-repl
julia> rad = RadialDblPower(3.0, 3.0)
julia> azi = AzimuthalUniform() # Defaults to Float64
julia> t = RingTemplate(rad, azi)
```
