```
INVALID_MODEL::TerminationStatusCode
```

An instance of the [`TerminationStatusCode`](@ref) enum.

## About

The algorithm stopped because the model is invalid.

The reason for this return code is solver-specific, but common causes are that the problem has zero variables or constraints, or that the problem data contains an invalid number such as `NaN`.
