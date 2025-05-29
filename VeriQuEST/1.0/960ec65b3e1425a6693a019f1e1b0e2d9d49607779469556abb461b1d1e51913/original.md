```
struct Dephasing <: NoiseModels
```

Dephasing noise model that represents noise caused by dephasing errors.

# Fields

  * `backend`: The backend used for simulation.
  * `type`: The type of qubits affected by the noise. Can be `SingleQubit` or `TwoQubits`.
  * `prob`: The probability of dephasing error. Can be a single value or a vector of probabilities.
