```
set_global!(sim::Simulation, name, value)
```

Set the value of the field `name` of the `globals` struct for simulation `sim`.

In parallel simulations, `set_global!` must be called on all processes, and with identical `value` across all processes.

`set_global!` must not be called within a transition function. 

See also [`create_simulation`](@ref), [`mapreduce`](@ref), [`modify_global!`](@ref) [`push_global!`](@ref) and [`get_global`](@ref)
