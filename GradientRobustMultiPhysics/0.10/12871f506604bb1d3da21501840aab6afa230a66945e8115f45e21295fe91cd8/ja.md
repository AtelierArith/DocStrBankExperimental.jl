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

ncomponentsが演算子評価の期待される長さである演算子評価のL2ノルムを計算するItemIntegratorを作成します。
