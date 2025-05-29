```
Langevin(; <keyword arguments>)
```

The Langevin integrator, based on the Langevin Middle Integrator in OpenMM.

See [Zhang et al. 2019](https://doi.org/10.1021/acs.jpca.9b02771). This is a leapfrog integrator, so the velocities are offset by half a time step behind the positions.

# Arguments

  * `dt::S`: the time step of the simulation.
  * `temperature::K`: the equilibrium temperature of the simulation.
  * `friction::F`: the friction coefficient of the simulation.
  * `coupling::C=NoCoupling()`: the coupling which applies during the simulation.
  * `remove_CM_motion=1`: remove the center of mass motion every this number of steps,   set to `false` or `0` to not remove center of mass motion.
