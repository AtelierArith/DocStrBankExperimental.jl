```
rotation_measure(n_cm3::Real, B_los::Real, dz::Real; ν_obs=nothing)
```

Computes the rotation measure of the parallel magnetic field along the LOS.

## Arguments

  * `n_cm3::Real`: Electron number density in [cm^-3].
  * `B_los::Real`: Magnetic field strength along the LOS in [G].

## Returns

  * `RM::Real`: Rotation measure in [rad/m^2].

## Mapping settings

  * weight function: [`part_weight_physical`](@ref)
  * reduce image: `false`
