```
AbstractUtilityReconstructionParameters{T <: AbstractImageReconstructionParameters}
```

Abstract type that offer utility functions for a given reconstruction parameter and its associated `process` steps. Utility `process` steps should return the same result as `T` for the same inputs.
