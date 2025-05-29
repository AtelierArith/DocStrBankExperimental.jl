```julia
struct BootstrapResult{S<:Real}
```

# Description

Structure to store bootstrap results.

# Fields

  * `moms`: simulated moments
  * `xs`: simulated parameter values
  * `sd_asymp`: asymptotic standard errors
  * `W`: efficient weighting matrix
