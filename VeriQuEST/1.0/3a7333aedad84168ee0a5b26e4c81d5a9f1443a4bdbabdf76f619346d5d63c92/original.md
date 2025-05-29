```
mutable struct Damping <: NoiseModels
```

A struct representing a damping noise model for a single qubit.

# Fields

  * `backend`: The backend used for simulation.
  * `type`: The type of noise model (SingleQubit).
  * `prob`: The probability of damping, can be a single value or a vector.
