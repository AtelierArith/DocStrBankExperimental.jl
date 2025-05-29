```
evolve_covar_and_ito_processes!(itoprocesses::Union{Dict{Symbol,ItoProcess{R}},Dict{Symbol,ItoProcess}}, covar::SimpleCovariance, new_time::Real; number_generator::NumberGenerator) where R<:Real
```

Evolve the `ItoProcess`es forward.

### Inputs

  * `itoprocesses` - A `Dict` of `ItoProcess`es
  * `covar` - The covariance matrix.
  * `new_time` - The new time.
  * `number_generator` - The number generator

### Return

  * The updated `ItoProcess`es
  * The Covariance matrix
