```
mer(
  weights::AbstractMatrix{T},
  rel_pr::AbstractMatrix{T},
  𝘷::T=0.
) where T<:AbstractFloat
```

投資の平均超過リターン（MER）を計算します。また、[`sn`](@ref)、[`ann_std`](@ref)、[`apy`](@ref)、[`ann_sharpe`](@ref)、[`mdd`](@ref)、[`calmar`](@ref)、および[`opsmetrics`](@ref)も参照してください。

# 引数

  * `weights::AbstractMatrix{T}`: ポートフォリオのウェイト。
  * `rel_pr::AbstractMatrix{T}`: 株式の相対価格。
  * `𝘷::T=0.`: 取引コスト率。

!!! warning
    `weights` と `rel_pr` のサイズは `(n_stocks, n_periods)` でなければなりません。


!!! note
    `size(rel_pr, 2)` が `size(weights, 2)` より大きい場合、`rel_pr` の最後の `size(weights, 2)` 列が使用されます。


# 戻り値

  * `MER::AbstractFloat`: 投資の平均超過リターン（MER）。
