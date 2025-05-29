```
modify_global!(sim::Simulation, name, f)
```

Modify the value of the `name` field of the `globals` structure for the simulation `sim` using the `f` function, which receives the current value as an argument.

This is a combination of [`set_global!`](@ref) and [`get_global`](@ref): `set_global!(sim, name, f(get_global(sim, name)))`.

`modify_global!` must not be called within a transition function.

In parallel simulations, `push_global!` must be called on all processes, and with identical `value` across all processes.

See also [`create_simulation`](@ref), [`mapreduce`](@ref), [`set_global!`](@ref) [`push_global!`](@ref) and [`get_global`](@ref)
