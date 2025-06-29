Empty placeholder for models that don't need an implied part. (For example, models that only regularize parameters.)

# Constructor

```
ImpliedEmpty(;specification, kwargs...)
```

# Arguments

  * `specification`: either a `RAMMatrices` or `ParameterTable` object

# Examples

A multigroup model with ridge regularization could be specified as a `SemEnsemble` with one model per group and an additional model with `ImpliedEmpty` and `SemRidge` for the regularization part.

# Extended help

## Interfaces

  * `param_labels(::ImpliedEmpty)`-> Vector of parameter labels
  * `nparams(::ImpliedEmpty)` -> Number of parameters
