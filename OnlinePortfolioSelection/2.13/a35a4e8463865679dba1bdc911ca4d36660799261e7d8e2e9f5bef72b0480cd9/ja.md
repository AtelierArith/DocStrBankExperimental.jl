```
ir(
  weights::AbstractMatrix{S},
  rel_pr::AbstractMatrix{S},
  rel_pr_market::AbstractVector{S};
  init_inv::S=1.
) where S<:AbstractFloat
```

ポートフォリオの情報比率 (IR) を計算します。また、[`sn`](@ref)、[`mer`](@ref)、[`ann_std`](@ref)、[`apy`](@ref)、[`ann_sharpe`](@ref)、[`mdd`](@ref)、[`calmar`](@ref)、および [`opsmetrics`](@ref) も参照してください。

ポートフォリオの情報比率 (IR) を計算するための公式は次のとおりです：

$$
IR = \frac{{{{\bar R}_s} - {{\bar R}_m}}}{{\sigma \left( {{R_s} - {R_m}} \right)}}
$$

ここで、$R_s$ はポートフォリオの日次リターン、$R_m$ は市場の日次リターン、$\bar R_s$ はポートフォリオの平均日次リターン、$\bar R_m$ は市場の平均日次リターン、$\sigma$ は市場に対するポートフォリオの日次超過リターンの標準偏差を表します。このパッケージでは、対数リターンが使用されることに注意してください。

# 引数

  * `weights::AbstractMatrix{S}`: ポートフォリオのウェイト。
  * `rel_pr::AbstractMatrix{S}`: 株式の相対価格。
  * `rel_pr_market::AbstractVector{S}`: 市場の相対価格。

## キーワード引数

  * `init_inv::S=1`: 初期投資額。

!!! warning
    `weights` と `rel_pr` のサイズは `(n_stocks, n_periods)` でなければなりません。


!!! note
    `size(rel_pr, 2)` が `size(weights, 2)` より大きい場合、`rel_pr` の最後の `size(weights, 2)` 列が使用されます。`rel_pr_market` のサイズは自動的に `w` のサイズに調整されます。


# 戻り値

  * `::AbstractFloat`: 投資期間のポートフォリオの情報比率 (IR)。

# 参考文献

> [Adaptive online portfolio strategy based on exponential gradient updates](https://doi.org/10.1007/s10878-021-00800-7)

