```julia
Multigrid(fineoperator, coarseoperator, smoother, prolongation, multigridtype)
```

有限要素演算子のためのマルチグリッド前処理器

# 引数:

  * `fineoperator::Operator`:                             前処理する有限要素演算子
  * `coarseoperator::Union{Operator,Multigrid}`:          前処理する有限要素演算子の粗いグリッド表現
  * `smoother::AbstractPreconditioner`:                   誤差緩和演算子、例えばヤコビ
  * `prolongationbases::AbstractArray{<:AbstractBasis}`:  粗いグリッドから細いグリッドへの要素延長基底
  * `multigridtype::MultigridType`:                       マルチグリッドの種類、h-マルチグリッドまたはp-マルチグリッド

# 戻り値:

  * マルチグリッド前処理器オブジェクト
