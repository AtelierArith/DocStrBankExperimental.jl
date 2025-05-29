```
RadialJohnsonSU(αinner, αouter)
```

Radial profile that given by positive unit radius Johnson SU distributions with the functional form

```julia
    exp[-1/2(γ + arcsinh((r - μ)/σ)²]*inv(1 + (r - 1)² + σ²)
```

where controls σ ≥ 0 the width, and γ the asymmetry.

## Notes

This is usually couple with a azimuthal profile to create a general ring template

```julia-repl
julia> rad = RadialJohnsonSU(1/2, -3/2)
julia> azi = AzimuthalUniform()
julia> t = RingTemplate(rad, azi)
```

## Arguments

  * `σ` : the width of the ring
  * `γ` : the asymmetry of the ring
