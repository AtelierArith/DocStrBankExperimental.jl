```
comptonY(n_cm3::Vector{<:Real}, T_K::Vector{<:Real}, z::Real)
```

Computes the Compton-Y parameter from electron density `n_cm3` and temperature `T` in Kelvin at redshift `z`.

## Arguments:

  * `n_cm3`: SPH particle density in [1/cm^3]
  * `T_K`: SPH particle temperature [K]
  * `z`: Redshift

## Mapping settings

  * weight function: [`part_weight_physical`](@ref)
  * reduce image: `false`
