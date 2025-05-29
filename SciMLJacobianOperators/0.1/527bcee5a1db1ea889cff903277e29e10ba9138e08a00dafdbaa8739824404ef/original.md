```
JacVecOperator(args...; autodiff = nothing, kwargs...)
```

Constructs a [`JacobianOperator`](@ref) which only provides the JVP using the `jvp_autodiff = autodiff`.
