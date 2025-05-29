```
opsmetrics(
  weights::AbstractMatrix{T},
  rel_pr::AbstractMatrix{T},
  rel_pr_market::AbstractVector{T};
  init_inv::T=1.,
  Rf::T=0.02
  dpy::S=252,
  v::T=0.
  dpy::S=252
) where {T<:AbstractFloat, S<:Int}
```

OPSアルゴリズムのメトリクスを計算します。また、[`sn`](@ref)、[`mer`](@ref)、[`ir`](@ref)、[`ann_std`](@ref)、[`apy`](@ref)、[`ann_sharpe`](@ref)、[`mdd`](@ref)、および[`calmar`](@ref)も参照してください。

# 引数

  * `weights::AbstractMatrix{T}`: ポートフォリオのウェイト。
  * `rel_pr::AbstractMatrix{T}`: 株式の相対価格。
  * `rel_pr_market::AbstractVector{T}`: 市場の相対価格。

## キーワード引数

  * `init_inv::T=1`: 初期投資額。
  * `Rf::T=0.02`: 無リスクの利回り。
  * `dpy::S=252`: 年間の日数。
  * `v::T=0.`: 取引コスト率。

!!! warning
    `weights`と`rel_pr`のサイズは`(n_stocks, n_periods)`でなければなりません。


!!! note
    `size(rel_pr, 2)`が`size(weights, 2)`より大きい場合、`rel_pr`の最後の`size(weights, 2)`列が使用されます。


# 戻り値

  * `::OPSMetrics`: [`OPSMetrics`](@ref)オブジェクト。
