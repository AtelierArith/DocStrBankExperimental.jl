```
elastic_collision!(a, b, f = nothing) → happened
```

Resolve a (hypothetical) elastic collision between the two agents `a, b`. They are assumed to be disks of equal size touching tangentially. Their velocities (field `vel`) are adjusted for an elastic collision happening between them. This function works only for two dimensions. Notice that collision only happens if both disks face each other, to avoid collision-after-collision.

If `f` is a `Symbol`, then the agent property `f`, e.g. `:mass`, is taken as a mass to weight the two agents for the collision. By default no weighting happens.

One of the two agents can have infinite "mass", and then acts as an immovable object that specularly reflects the other agent. In this case momentum is not conserved, but kinetic energy is still conserved.

Return a boolean encoding whether the collision happened.

Example usage in [Continuous space social distancing]( https://juliadynamics.github.io/AgentsExampleZoo.jl/dev/examples/social_distancing/).
