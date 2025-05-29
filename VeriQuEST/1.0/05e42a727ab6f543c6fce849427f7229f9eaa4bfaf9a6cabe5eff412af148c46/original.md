```
mutable struct Pauli <: NoiseModels
```

The `Pauli` struct represents a noise model for a single qubit. It contains the following fields:

  * `backend`: The backend used for simulation.
  * `type`: The type of noise model (SingleQubit).
  * `prob`: The probability of each Pauli error. It can be a single value, a vector of values, or a matrix of values.
