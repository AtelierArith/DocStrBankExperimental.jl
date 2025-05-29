```
StormerVerlet(; <keyword arguments>)
```

The Störmer-Verlet integrator.

The velocity calculation is accurate to O(dt).

Does not currently work with coupling methods that alter the velocity. Does not currently remove the center of mass motion.

# Arguments

  * `dt::T`: the time step of the simulation.
  * `coupling::C=NoCoupling()`: the coupling which applies during the simulation.
