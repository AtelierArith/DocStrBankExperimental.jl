```
ann_std(cum_ret::AbstractVector{AbstractFloat}; dpy)
```

ポートフォリオの年率標準偏差 ($\sigma_p$) を計算します。また、[`sn`](@ref)、[`mer`](@ref)、[`apy`](@ref)、[`ann_sharpe`](@ref)、[`mdd`](@ref)、[`calmar`](@ref)、および [`opsmetrics`](@ref) も参照してください。

# 引数

  * `cum_ret::AbstractVector{AbstractFloat}`: 投資期間中の累積資産。

## キーワード引数

  * `dpy`: 1年の日数。

# 戻り値

  * `::AbstractFloat`: ポートフォリオの年率標準偏差 ($\sigma_p$)。
