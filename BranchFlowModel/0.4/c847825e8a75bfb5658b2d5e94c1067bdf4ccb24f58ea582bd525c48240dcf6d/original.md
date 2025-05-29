```
build_bfm!(m::JuMP.AbstractModel, net::Network{SinglePhase}, ::Val{Unrelaxed})
```

Add variables and constraints to `m` using the values in `net`. Calls the following functions:

```julia
add_linear_variables(m, net)
add_vsqrd_variables(m, net)
add_isqrd_variables(m, net)
constrain_power_balance_with_isqrd_losses(m, net)
constrain_substation_voltage(m, net)
constrain_KVL(m, net)
constrain_bilinear(m, net)
```
