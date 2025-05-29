```julia
L2ErrorIntegrator(
    compare_data::GradientRobustMultiPhysics.AbstractUserDataType;
    ...
) -> GradientRobustMultiPhysics.AssemblyPattern{ItemIntegrator, T, AT, Float64, Int32, GradientRobustMultiPhysics.DefaultUserAction{T1, Ti, dx, dt, di, dl, ndim, KernelType}} where {T<:Real, AT<:ExtendableGrids.AssemblyType, T1, Ti, dx, dt, di, dl, ndim, KernelType}
L2ErrorIntegrator(
    compare_data::GradientRobustMultiPhysics.AbstractUserDataType,
    operator;
    T,
    quadorder,
    name,
    AT,
    factor,
    regions,
    time
) -> GradientRobustMultiPhysics.AssemblyPattern{ItemIntegrator, T, AT, Float64, Int32, GradientRobustMultiPhysics.DefaultUserAction{T1, Ti, dx, dt, di, dl, ndim, KernelType}} where {T<:Real, AT<:ExtendableGrids.AssemblyType, T1, Ti, dx, dt, di, dl, ndim, KernelType}

```

Creates an ItemIntegrator that compares discrete FEVectorBlock operator-evaluations against the given compare*data and returns the L2-error || compare*data(x) - factor*discrete(x) ||. If quadorder is left on "auto" two times the quadorder of the data is used in the evaluation.
