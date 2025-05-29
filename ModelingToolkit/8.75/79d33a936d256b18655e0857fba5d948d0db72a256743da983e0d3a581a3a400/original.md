```julia
generate_jacobian(sys::AbstractSystem, dvs = states(sys), ps = parameters(sys),
                  expression = Val{true}; sparse = false, kwargs...)
```

Generates a function for the Jacobian matrix of a system. Extra arguments control the arguments to the internal [`build_function`](@ref) call.
