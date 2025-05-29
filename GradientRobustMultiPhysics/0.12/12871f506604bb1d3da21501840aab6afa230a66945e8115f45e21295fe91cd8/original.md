```julia
L2NormIntegrator(
    ncomponents::Int64,
    operator;
    T,
    AT,
    name,
    quadorder,
    regions
) -> GradientRobustMultiPhysics.AssemblyPattern{ItemIntegrator, T, AT, Float64, Int32, GradientRobustMultiPhysics.DefaultUserAction{T1, Ti, dx, dt, di, dl, ndim, KernelType}} where {T<:Real, AT<:ExtendableGrids.AssemblyType, T1, Ti, dx, dt, di, dl, ndim, KernelType}

```

Creates an ItemIntegrator that computes the L2 norm of an operator evaluation where ncomponents is the expected length of the operator evaluation.
