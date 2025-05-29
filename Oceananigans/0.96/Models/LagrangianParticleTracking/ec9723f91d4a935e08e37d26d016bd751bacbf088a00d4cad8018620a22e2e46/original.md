```
LagrangianParticles(particles::StructArray; restitution=1.0, tracked_fields::NamedTuple=NamedTuple(), dynamics=no_dynamics)
```

Construct some `LagrangianParticles` that can be passed to a model. The `particles` should be a `StructArray` and can contain custom fields. The coefficient of restitution for particle-wall collisions is specified by `restitution`.

A number of `tracked_fields` may be passed in as a `NamedTuple` of fields. Each particle will track the value of each field. Each tracked field must have a corresponding particle property. So if `T` is a tracked field, then `T` must also be a custom particle property.

`dynamics` is a function of `(lagrangian_particles, model, Δt)` that is called prior to advecting particles. `parameters` can be accessed inside the `dynamics` function.
