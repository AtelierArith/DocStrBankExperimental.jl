```
rotation_measure(n_cm3::Real, B_los::Real, dz::Real, ν_obs::Real)
```

Computes the rotation measure of the parallel magnetic field along the LOS at a given frequency. To be used for continuous rotation of polarized emission along the LOS.

## Arguments

  * `n_cm3::Real`: Electron number density in [cm^-3].
  * `B_los::Real`: Magnetic field strength along the LOS in [G].
  * `dz::Real`: Depth along the LOS in [cm]. See [`get_dz`](@ref) for a convenient helper function.
  * `ν_obs::Real`: Observing frequency in [Hz].

## Returns

  * `RM::Real`: Rotation measure in [rad/cm^2].

## Mapping settings

  * weight function: [`part_weight_physical`](@ref)
  * reduce image: `false`
  * stokes: `true`
  * sort_z: `true`
  * `RM`: use output of this function.
