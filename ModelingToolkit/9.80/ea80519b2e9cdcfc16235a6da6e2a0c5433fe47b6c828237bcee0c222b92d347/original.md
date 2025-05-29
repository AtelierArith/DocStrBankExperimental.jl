```julia
generate_function(sys::AbstractSystem, dvs = unknowns(sys), ps = parameters(sys),
                  expression = Val{true}; kwargs...)
```

Generate a function to evaluate the system's equations.
