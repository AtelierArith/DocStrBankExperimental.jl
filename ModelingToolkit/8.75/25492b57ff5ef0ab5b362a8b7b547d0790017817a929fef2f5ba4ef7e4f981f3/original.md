```julia
generate_factorized_W(sys::AbstractSystem, dvs = states(sys), ps = parameters(sys),
                      expression = Val{true}; sparse = false, kwargs...)
```

Generates a function for the factorized W matrix of a system. Extra arguments control the arguments to the internal [`build_function`](@ref) call.
