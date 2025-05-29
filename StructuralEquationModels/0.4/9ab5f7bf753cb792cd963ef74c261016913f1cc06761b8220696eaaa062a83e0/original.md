Maximum likelihood estimation.

# Constructor

```
SemML(;observed, meanstructure = false, approximate_hessian = false, kwargs...)
```

# Arguments

  * `observed::SemObserved`: the observed part of the model
  * `meanstructure::Bool`: does the model have a meanstructure?
  * `approximate_hessian::Bool`: if hessian-based optimization is used, should the hessian be swapped for an approximation

# Examples

```julia
my_ml = SemML(observed = my_observed)
```

# Interfaces

Analytic gradients are available, and for models without a meanstructure and RAMSymbolic implied type, also analytic hessians.
