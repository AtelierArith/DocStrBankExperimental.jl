```
exogenous_outputs(sys)
```

Get the vector of exogenous output connectors of the system represented by the process element `sys`.

This function returns the exogenous outputs of the system. Exogenous outputs are all outputs of the system which are not connectors provided by this package, i.e. not flows, states nor rates.

# Extended Help

# Implementation

This function should be overridden for each type inheriting from [`AbstractProcessElement`](@ref) which could have one or more exogenous outputs.
