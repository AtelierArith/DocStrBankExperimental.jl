```
OverdampedLangevin(; <keyword arguments>)
```

Simulates the overdamped Langevin equation using the Euler-Maruyama method.

Not currently compatible with constraints, will print a warning and continue without applying constraints.

# Arguments

  * `dt::S`: the time step of the simulation.
  * `temperature::K`: the equilibrium temperature of the simulation.
  * `friction::F`: the friction coefficient of the simulation.
  * `remove_CM_motion=1`: remove the center of mass motion every this number of steps,   set to `false` or `0` to not remove center of mass motion.
