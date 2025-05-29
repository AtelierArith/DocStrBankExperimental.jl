```
build_bfm!(m::JuMP.AbstractModel, net::Network{MultiPhase}, ::Val{Linear})
```

Add variables and constraints to `m` using the values in `net`. Calls the following functions:

  * [`add_linear_variables`](@ref)
