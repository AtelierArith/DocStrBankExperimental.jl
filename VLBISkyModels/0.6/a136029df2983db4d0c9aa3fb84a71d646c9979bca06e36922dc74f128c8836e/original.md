```
AzimuthalCosine(s::NTuple{N,T}, ξ::NTuple{N, T}) where {N, T}
```

A azimuthal profile that is  given by a cosine expansion of order `N`. The expansion is given by

```
    1 - ∑ₙ sₙcos(nϕ - ξₙ)
```

## Notes

This is usually couple with a radial profile to create a general ring template

```julia-repl
julia> rad = RadialDblPower(3.0, 3.0)
julia> azi = AzimuthalCosine((0.5, 0.2), (0.0, π/4)) # Defaults to Float64
julia> t = RingTemplate(rad, azi)
```

## Arguments

  * `s` : amplitudes of the `N` order cosine expansion of the azimuthal brightness
  * `ξs`: phase of the `N` order cosine expansion of the azimuthal brightness
