```
set_va!(body_aero::BodyAerodynamics, va::VelVector, omega=zeros(MVec3))
```

Set velocity array and update wake filaments.

# Arguments

  * body_aero::BodyAerodynamics: The [BodyAerodynamics](@ref) struct to modify
  * `va::VelVector`: Velocity vector of the apparent wind speed           [m/s]
  * `omega::VelVector`: Turn rate vector around x y and z axis            [rad/s]
