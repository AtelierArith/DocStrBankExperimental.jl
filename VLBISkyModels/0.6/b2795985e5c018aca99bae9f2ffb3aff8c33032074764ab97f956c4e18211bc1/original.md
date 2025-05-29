```
RadialTruncExp(σ)
```

Radial profile that has a exponential profile up to a cutoff radius of 1 where for `r<1` the profile is identically zero.

This evalutes to

```julia
    exp(-(r-1)/σ)
```

## Notes

This is usually couple with a azimuthal profile to create a general ring template

```julia-repl
julia> rad = RadialTruncExp(2.0)
julia> azi = AzimuthalUniform()
julia> t = RingTemplate(rad, azi)
```

## Arguments

  * `σ`: Exponential inverse fall off parameter.
