```julia
generate_function(sys::AbstractSystem, dvs = states(sys), ps = parameters(sys),
                  expression = Val{true}; kwargs...)
```

Generate a function to evaluate the system's equations.
