```
VecJacOperator(args...; autodiff = nothing, kwargs...)
```

Constructs a [`JacobianOperator`](@ref) which only provides the VJP using the `vjp_autodiff = autodiff`.
