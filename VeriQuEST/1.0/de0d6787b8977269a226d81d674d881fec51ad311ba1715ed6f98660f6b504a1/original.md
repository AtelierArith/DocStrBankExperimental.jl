```
struct Kraus <: NoiseModels
```

A struct representing a noise model using Kraus operators.

# Fields

  * `backend`: The backend used for the noise model.
  * `type`: The type of noise model, which can be `SingleQubit`, `TwoQubits`, or `MultipleQubits`.
