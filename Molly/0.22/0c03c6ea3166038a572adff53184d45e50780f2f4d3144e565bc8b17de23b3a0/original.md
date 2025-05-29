```
Verlet(; <keyword arguments>)
```

The leapfrog Verlet integrator.

This is a leapfrog integrator, so the velocities are offset by half a time step behind the positions.

# Arguments

  * `dt::T`: the time step of the simulation.
  * `coupling::C=NoCoupling()`: the coupling which applies during the simulation.
  * `remove_CM_motion=1`: remove the center of mass motion every this number of steps,   set to `false` or `0` to not remove center of mass motion.
