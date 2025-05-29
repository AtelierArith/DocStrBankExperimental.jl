```
build_ldf!(m::JuMP.AbstractModel, p::Inputs)
```

Add variables and constraints to `m` using the values in `p`. Calls the following functions:

```julia
add_variables(m, p)
constrain_power_balance(m, p)
constrain_substation_voltage(m, p)
constrain_KVL(m, p)
constrain_loads(m, p)
```
