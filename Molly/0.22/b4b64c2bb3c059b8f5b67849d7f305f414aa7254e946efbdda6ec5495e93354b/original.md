```
NoseHoover(; <keyword arguments>)
```

The Nosé-Hoover integrator, a NVT simulator that extends velocity Verlet to control the temperature of the system.

See [Evans and Holian 1985](https://doi.org/10.1063/1.449071). The current implementation is limited to ergodic systems.

Not currently compatible with constraints, will print a warning and continue without applying constraints.

# Arguments

  * `dt::T`: the time step of the simulation.
  * `temperature::K`: the equilibrium temperature of the simulation.
  * `damping::D=100*dt`: the temperature damping time scale.
  * `coupling::C=NoCoupling()`: the coupling which applies during the simulation.
  * `remove_CM_motion=1`: remove the center of mass motion every this number of steps,   set to `false` or `0` to not remove center of mass motion.
