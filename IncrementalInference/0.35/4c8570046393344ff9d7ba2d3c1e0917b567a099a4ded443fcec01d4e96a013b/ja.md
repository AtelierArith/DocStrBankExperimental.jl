```julia
propagateBelief(
    dfg,
    destvar,
    factors;
    solveKey,
    dens,
    N,
    needFreshMeasurements,
    dbg,
    logger,
    asPartial
)

```

`dfg`のファクターを使用して`destvert`の提案と積を計算します。

ノート

  * 積のタプルと、全次元（=true）または部分次元（=false）であるかどうかを返します。
  * `N`は周辺から引き出すサンプルの数を決定します。
  * `dens`は混合された全次元および部分次元の`ManifoldKernelDensity`信念を含むことができます。

関連

[`approxConvBelief`](@ref), [`proposalbeliefs!`](@ref), [`AMP.manifoldProduct`](@ref)
