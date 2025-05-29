```julia
struct BaseDiagnostics{P}
```

Stores summary information for diagnostics output that is included in all Baytes kernels.

# Fields

  * `ℓobjective::Float64`: Log objective target result.
  * `temperature::Float64`: Temperature for target result
  * `prediction::Any`: Prediction of future data.
  * `iter::Int64`: Current iteration of kernel.
