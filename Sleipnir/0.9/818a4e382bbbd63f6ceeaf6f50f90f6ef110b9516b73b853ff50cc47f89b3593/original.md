```
IntegratedTrajectoryMapping <: VelocityMapping
```

Integrated trajectory mapping. This mapping is closer to reality as it consists in integrating over time the instantaneous ice surface velocities along ice flow trajectories in a Lagrangian way. This integrated velocity is then compared to the velocity of the datacube. It has not been implemented yet but its computational cost will likely be expensive.

# Fields

  * `spatialInterp::Symbol`: The spatial interpolation to use to map the ice surface   velocity grid to the glacier grid. For the moment only `:nearest` is supported.
