```julia
generate_hessian(sys::AbstractSystem, dvs = states(sys), ps = parameters(sys),
                 expression = Val{true}; sparse = false, kwargs...)
```

Generates a function for the hessian matrix of a system. Extra arguments control the arguments to the internal [`build_function`](@ref) call.
