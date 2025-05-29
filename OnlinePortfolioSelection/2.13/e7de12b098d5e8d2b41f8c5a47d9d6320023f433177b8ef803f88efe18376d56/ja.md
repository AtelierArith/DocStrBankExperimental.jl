```
at(rel_pr::AbstractMatrix, b::AbstractMatrix)
```

ポートフォリオの平均回転率を計算します。また、[`sn`](@ref)、[`mer`](@ref)、[`ir`](@ref)、[`ann_std`](@ref)、[`apy`](@ref)、[`ann_sharpe`](@ref)、[`mdd`](@ref)、および[`calmar`](@ref)も参照してください。

# 引数

  * `rel_pr::AbstractMatrix`: 株式の相対価格。
  * `b::AbstractMatrix`: ポートフォリオのウェイト。

# 戻り値

  * `::AbstractFloat`: ポートフォリオの平均回転率。
