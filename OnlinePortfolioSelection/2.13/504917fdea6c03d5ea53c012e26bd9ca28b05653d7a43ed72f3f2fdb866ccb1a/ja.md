```
apy(Sn::AbstractFloat, n_periods::S; dpy::S=252) where S<:Int
```

投資の年間パーセンテージ利回り（APY）を計算します。また、[`sn`](@ref)、[`mer`](@ref)、[`ann_std`](@ref)、[`ann_sharpe`](@ref)、[`mdd`](@ref)、[`calmar`](@ref)、および[`opsmetrics`](@ref)も参照してください。

# 引数

  * `Sn::AbstractFloat`: 投資の累積資産。
  * `n_periods::S`: 投資期間の数。
  * `dpy::S=252`: 1年の日数。

# 戻り値

  * `::AbstractFloat`: 投資のAPY。
