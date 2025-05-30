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

アイテムインテグレーターを作成し、離散FEVectorBlockオペレーター評価を指定されたcompare*dataと比較し、L2誤差|| compare*data(x) - factor*discrete(x) ||を返します。quadorderが「auto」のままの場合、評価にはデータのquadorderの2倍が使用されます。
