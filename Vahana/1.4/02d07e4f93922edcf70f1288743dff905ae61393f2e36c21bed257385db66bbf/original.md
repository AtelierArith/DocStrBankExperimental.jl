```
push_global!(sim::Simulation, name, value)
```

In the case that a field of the `globals` struct from the Simulation constructor is a vector (e.g. for time series data), `push_global!` can be used to add a value to this vector, instead of writing `set_global!(sim, name, push!(get_global(sim, name), value)`.

In parallel simulations, `push_global!` must be called on all processes, and with identical `value` across all processes.

`push_global!` must not be called within a transition function. 

See also [`create_model`](@ref), [`mapreduce`](@ref), [`set_global!`](@ref) and [`get_global`](@ref)
