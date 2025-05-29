```julia
L2DifferenceIntegrator(
    ncomponents::Int64,
    operator;
    AT,
    T,
    name,
    quadorder,
    regions
) -> GradientRobustMultiPhysics.AssemblyPattern{ItemIntegrator, T, AT, Float64, Int32, GradientRobustMultiPhysics.DefaultUserAction{T1, Ti, dx, dt, di, dl, ndim, KernelType}} where {T<:Real, AT<:ExtendableGrids.AssemblyType, T1, Ti, dx, dt, di, dl, ndim, KernelType}

```

Creates an ItemIntegrator that computes the L2 norm difference between two arguments evalauted with the same operator (or with different operators if operator is an array) where ncomponents is the expected length of each operator evaluation. Note that all arguments in an evaluation call need to be defined on the same grid !
