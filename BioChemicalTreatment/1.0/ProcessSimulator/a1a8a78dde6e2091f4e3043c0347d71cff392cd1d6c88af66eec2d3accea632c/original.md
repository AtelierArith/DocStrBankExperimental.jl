```
exogenous_inputs(sys)
```

Get the vector of exogenous input connectors of the system represented by the process element `sys`.

This function returns the exogenous inputs of the system. Exogenous inputs are all inputs to the system which are not connectors provided by this package, i.e. not flows, states nor rates.

# Extended Help

# Implementation

This function should be overridden for each type inheriting from [`AbstractProcessElement`](@ref) which could have one or more exogenous inputs.
