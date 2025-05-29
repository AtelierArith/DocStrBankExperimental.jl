```julia
calculate_jacobian(sys::AbstractSystem)
```

Calculate the Jacobian matrix of a system.

Returns a matrix of [`Num`](@ref) instances. The result from the first call will be cached in the system object.
