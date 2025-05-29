```
thermal_SZ( n_cm3::Vector{<:Real}, T_K::Vector{<:Real},
            z::Real=0.0, ν::Real=1.44e9; 
            DI_over_I::Bool=false )
```

Computes the thermal Sunyaev-Zel'dovich effect for electron density `n_cm3` and temperature `T_K` in Kelvin at redshift `z` and observer frequency `ν`. `DI_over_I` outputs in units of $dI/I$ if set to `true` and `dT/T` otherwise.

## Arguments:

  * `n_cm3`: SPH particle density in [1/cm^3]
  * `T_K`: SPH particle temperature [K]
  * `z`: Redshift
  * `ν`: Observing frequency

## Mapping settings

  * weight function: [`part_weight_physical`](@ref)
  * reduce image: `false`
