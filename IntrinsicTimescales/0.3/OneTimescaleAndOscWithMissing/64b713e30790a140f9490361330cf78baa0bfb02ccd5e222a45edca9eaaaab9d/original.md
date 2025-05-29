```
int_fit(model::OneTimescaleAndOscWithMissingModel, param_dict=nothing)
```

Perform inference using the specified fitting method.

# Arguments

  * `model::OneTimescaleAndOscWithMissingModel`: Model instance
  * `param_dict=nothing`: Optional dictionary of algorithm parameters. If nothing, uses defaults.

# Returns

For ABC method:

  * `posterior_samples`: Matrix of accepted parameter samples
  * `posterior_MAP`: Maximum a posteriori estimate
  * `abc_record`: Full record of ABC iterations

For ADVI method:

  * `ADVIResults`: Container with samples, MAP estimates, variances, and full chain

# Notes

  * For ABC: Uses Population Monte Carlo ABC with adaptive epsilon selection
  * For ADVI: Uses Automatic Differentiation Variational Inference via Turing.jl
  * Parameter dictionary can be customized for each method (see get*param*dict_abc())
