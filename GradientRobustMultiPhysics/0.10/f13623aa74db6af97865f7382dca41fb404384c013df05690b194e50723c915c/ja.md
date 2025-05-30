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

アイテムインテグレーターを作成し、与えられた compare*data に対して離散 FEVectorBlock 演算子評価を比較し、L2誤差 || compare*data(x) - factor*discrete(x) || を返します。quadorder が "auto" のままの場合、評価にはデータの quadorder の2倍が使用されます。
