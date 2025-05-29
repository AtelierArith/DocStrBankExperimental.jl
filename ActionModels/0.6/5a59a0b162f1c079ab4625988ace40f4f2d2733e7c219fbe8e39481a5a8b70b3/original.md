```
get_parameters(agent::Agent, target_param::Union{String,Tuple})
```

Get a single parameter from an agent. Returns a single value.

```
get_parameters(agent::Agent, target_param::Vector)
```

Get a set of parameter values from an agent. Returns a dictionary of parameters and their values.

```
get_parameters(agent::Agent)
```

Get all parameters from an agent. Returns a dictionary of parameters and their values.
