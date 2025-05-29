Full information maximum likelihood estimation. Can handle observed data with missings.

# Constructor

```
SemFIML(;observed, specification, kwargs...)
```

# Arguments

  * `observed::SemObservedMissing`: the observed part of the model
  * `specification`: either a `RAMMatrices` or `ParameterTable` object

# Examples

```julia
my_fiml = SemFIML(observed = my_observed, specification = my_parameter_table)
```

# Interfaces

Analytic gradients are available.
