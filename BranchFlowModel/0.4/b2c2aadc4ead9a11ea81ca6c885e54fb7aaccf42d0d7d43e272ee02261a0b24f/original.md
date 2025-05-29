```
build_bfm!(m::JuMP.AbstractModel, net::Network{MultiPhase}, ::Val{Unrelaxed})
```

Add variables and constraints to `m` using the values in `net` to make an unrelaxed branch flow model. Calls the following functions:

  * [`add_bfm_variables`](@ref)
  * [`constrain_bfm_nlp`](@ref)

```
