```
RadialDblPower(αinner, αouter)
```

Radial profile that given by a double power-law with the function form

```julia
    r^αinner*inv(1+ r^(αinner + αouter + 1))
```

## Notes

This is usually couple with a azimuthal profile to create a general ring template

```julia-repl
julia> rad = RadialDblPower(3.0, 3.0)
julia> azi = AzimuthalUniform()
julia> t = RingTemplate(rad, azi)
```

## Arguments

  * `αinner` the power law index for `r<1`.
  * `αouter` the power law index for `r≥1`.
