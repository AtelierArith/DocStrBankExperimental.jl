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

同じ演算子（または演算子が配列の場合は異なる演算子）で評価された2つの引数間のL2ノルムの差を計算するItemIntegratorを作成します。ncomponentsは各演算子評価の期待される長さです。評価呼び出しのすべての引数は同じグリッド上で定義されている必要があることに注意してください！
