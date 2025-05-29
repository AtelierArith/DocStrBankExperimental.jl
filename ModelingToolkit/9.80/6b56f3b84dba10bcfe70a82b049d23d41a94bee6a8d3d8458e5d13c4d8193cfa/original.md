```julia
generate_gradient(sys::AbstractSystem, dvs = unknowns(sys), ps = parameters(sys),
                  expression = Val{true}; kwargs...)
```

Generates a function for the gradient of a system. Extra arguments control the arguments to the internal [`build_function`](@ref) call.
