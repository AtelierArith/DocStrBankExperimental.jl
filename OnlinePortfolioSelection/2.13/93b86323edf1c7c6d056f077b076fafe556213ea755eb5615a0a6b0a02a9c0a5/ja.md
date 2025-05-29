```
ann_sharpe(APY::T, Rf::T, sigma_prtf::T) where T<:AbstractFloat
```

投資の年率シャープ比を計算します。また、[`sn`](@ref)、[`mer`](@ref)、[`ann_std`](@ref)、[`apy`](@ref)、[`mdd`](@ref)、[`calmar`](@ref)、および[`opsmetrics`](@ref)も参照してください。

# 引数

  * `APY::T`: 投資のAPY。
  * `Rf::T`: 無リスクのリターン率。
  * `sigma_prtf::T`: ポートフォリオの標準偏差 $\sigma_p$。

# 戻り値

  * `::AbstractFloat`: 投資の年率シャープ比。
