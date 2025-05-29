```
kinetic_SZ(n_cm3::Real, vel_y_cgs::Real, 
           z::Real=0.0, ν::Real=1.e9;
           DI_over_I::Bool=false)
```

Computes the kinetic Sunyaev-Zel'dovich effect from electron density `n_cm3` and velocity in y-direction to the projection plane in cgs units `vel_y_cgs`. If `DI_over_I` is set to `true` you also need to provide an observation frequency `ν` and redshift `z`.

## Arguments:

  * `n_cm3`: SPH particle density in [1/cm^3]
  * `vel_y_cgs`: SPH particle velocity in y-direction in [cm/s]
  * `z`: Redshift
  * `ν`: Observing frequency

## Mapping settings

  * weight function: [`part_weight_physical`](@ref)
  * reduce image: `false`
