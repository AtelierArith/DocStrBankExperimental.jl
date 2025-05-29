```julia
calcFactorResidualTemporary(
    fct,
    varTypes,
    measurement,
    pts;
    tfg,
    _blockRecursion,
    doTime
)

```

単一サンプルの残差関数を評価します。

ノート

  * この段階ではバイナリ因子のみであり、`multihypo`はこのテストで考慮する必要はありません
  * 計算は単一の粒子に対して行われると仮定しているため、`meas::Tuple{Z,other}`は単一の粒子の値のみです。

例

```julia
residual = calcFactorResidualTemporary(Pose2Pose2(...), (RoME.Pose2,RoME.Pose2), (z_i,), (x1, x2))
```

関連

[`calcFactorResidual`](@ref), [`CalcResidual`](@ref), [`_evalFactorTemporary!`](@ref), [`approxConvBelief`](@ref), [`_buildGraphByFactorAndTypes!`](@ref)
