```
LagrangianParticles(; x, y, z, restitution=1.0, dynamics=no_dynamics, parameters=nothing)
```

Construct some `LagrangianParticles` that can be passed to a model. The particles will have initial locations `x`, `y`, and `z`. The coefficient of restitution for particle-wall collisions is specified by `restitution`.

`dynamics` is a function of `(lagrangian_particles, model, Δt)` that is called prior to advecting particles. `parameters` can be accessed inside the `dynamics` function.
