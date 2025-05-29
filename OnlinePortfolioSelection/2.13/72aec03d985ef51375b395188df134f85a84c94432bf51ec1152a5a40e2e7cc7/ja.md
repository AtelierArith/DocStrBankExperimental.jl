```
calmar(APY::T, MDD::T) where T<:AbstractFloat
```

投資のカルマ比率を計算します。また、[`sn`](@ref)、[`mer`](@ref)、[`ann_std`](@ref)、[`apy`](@ref)、[`ann_sharpe`](@ref)、[`mdd`](@ref)、および[`opsmetrics`](@ref)も参照してください。

# 引数

  * `APY::T`: 投資のAPY。
  * `MDD::T`: 投資のMDD。

# 戻り値

  * `::AbstractFloat`: 投資のカルマ比率。
