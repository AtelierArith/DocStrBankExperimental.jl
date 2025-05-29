```
random_velocities!(sys, temp; rng=Random.default_rng())
random_velocities!(vels, sys, temp; rng=Random.default_rng())
```

Set the velocities of a [`System`](@ref), or a vector, to random velocities generated from the Maxwell-Boltzmann distribution.
