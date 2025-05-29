```
LangevinSplitting(; <keyword arguments>)
```

The Langevin simulator using a general splitting scheme.

This consists of a succession of **A**, **B** and **O** steps, corresponding respectively to updates in position, velocity for the potential part, and velocity for the thermal fluctuation-dissipation part. The [`Langevin`](@ref) and [`VelocityVerlet`](@ref) simulators without coupling correspond to the **BAOA** and **BAB** schemes respectively. For more information on the sampling properties of splitting schemes, see [Fass et al. 2018](https://doi.org/10.3390/e20050318).

Not currently compatible with constraints, will print a warning and continue without applying constraints.

# Arguments

  * `dt::S`: the time step of the simulation.
  * `temperature::K`: the equilibrium temperature of the simulation.
  * `friction::F`: the friction coefficient. If units are used, it should have a   dimensionality of mass per time.
  * `splitting::W`: the splitting specifier. Should be a string consisting of the   characters `A`, `B` and `O`. Strings with no `O`s reduce to deterministic   symplectic schemes.
  * `remove_CM_motion=1`: remove the center of mass motion every this number of steps,   set to `false` or `0` to not remove center of mass motion.
