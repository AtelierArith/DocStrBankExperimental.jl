```
DETPFlash(; numphases = 2,
max_steps = 1e4*(numphases-1),
population_size =20,
time_limit = Inf,
verbose = false,
logspace = false,
equilibrium = :auto)
```

Method to solve non-reactive multicomponent flash problem by finding global minimum of Gibbs Free Energy via Differential Evolution.

User must assume a number of phases, `numphases`. If true number of phases is smaller than numphases, model should predict either (a) identical composition in two or more phases, or (b) one phase with negligible total number of moles. If true number of phases is larger than numphases, a thermodynamically unstable solution will be predicted.

The optimizer will stop at `max_steps` evaluations or at `time_limit` seconds

The `equilibrium` keyword allows to restrict the search of phases to just liquid-liquid equilibria (`equilibrium = :lle`). the default searches for liquid and gas phases.
