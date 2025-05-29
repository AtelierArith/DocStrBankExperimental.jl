```
mutable struct Depolarising <: NoiseModels
```

A struct representing a depolarizing noise model.

# Fields

  * `backend`: The backend used for the noise model.
  * `type`: The type of qubits affected by the noise model.
  * `prob`: The probability of depolarization, can be a single value or a vector.
