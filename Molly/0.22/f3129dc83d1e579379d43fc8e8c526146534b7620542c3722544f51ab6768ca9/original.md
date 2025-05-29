```
SHAKE_RATTLE(constraints, n_atoms, dist_tolerance, vel_tolerance)
```

Constrain distances during a simulation using the SHAKE and RATTLE algorithms.

Velocity constraints will be imposed for simulators that integrate velocities such as [`VelocityVerlet`](@ref). See [Ryckaert et al. 1977](https://doi.org/10.1016/0021-9991(77)90098-5) for SHAKE, [Andersen 1983](https://doi.org/10.1016/0021-9991(83)90014-1) for RATTLE and [Elber et al. 2011](https://doi.org/10.1140%2Fepjst%2Fe2011-01525-9) for a derivation of the linear system solved to satisfy the RATTLE algorithm.

Not currently compatible with GPU simulation.

# Arguments

  * `constraints`: a vector of constraints to be imposed on the system.
  * `n_atoms::Integer`: the number of atoms in the system.
  * `dist_tolerance`: the tolerance used to end the iterative procedure when calculating   position constraints, should have the same units as the coordinates.
  * `vel_tolerance`: the tolerance used to end the iterative procedure when calculating   velocity constraints, should have the same units as the velocities * the coordinates.
