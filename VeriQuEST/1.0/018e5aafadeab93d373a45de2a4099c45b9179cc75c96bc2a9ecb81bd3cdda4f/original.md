```
mutable struct MixtureDensityMatrices <: NoiseModels
```

A mutable struct representing a mixture of density matrices noise model.

# Fields

  * `backend`: The backend used for the noise model.
  * `type`: The type of density matrices.
  * `prob`: The probability distribution of the mixture.
