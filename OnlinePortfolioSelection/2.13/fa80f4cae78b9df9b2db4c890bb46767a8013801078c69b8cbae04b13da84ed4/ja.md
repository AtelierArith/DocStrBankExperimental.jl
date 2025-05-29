```
sn(weights::AbstractMatrix{T}, rel_pr::AbstractMatrix{T}; init_inv::T=1.) where T<:AbstractFloat
```

ポートフォリオの累積資産を一定期間にわたって計算します。また、[`mer`](@ref)、[`ann_std`](@ref)、[`apy`](@ref)、[`ann_sharpe`](@ref)、[`mdd`](@ref)、[`calmar`](@ref)、および[`opsmetrics`](@ref)も参照してください。

ポートフォリオの累積資産を計算するための式は次のとおりです：

$$
{S_n} = {S_0}\prod\limits_{t = 1}^T {\left\langle {{b_t},{x_t}} \right\rangle }
$$

ここで、$S_0$は初期予算、$n$は投資の期間、$b_t$は期間$t$の重みのベクトル、$x_t$は$t$-th期間の相対価格です。

# 引数

  * `weights::AbstractMatrix{T}`: ポートフォリオの重み。
  * `rel_pr::AbstractMatrix{T}`: 株式の相対価格。

## キーワード引数

  * `init_inv::T=1`: 初期投資。

!!! warning "注意！"
    `weights`と`rel_pr`のサイズは`(n_stocks, n_periods)`でなければなりません。


!!! note
    `size(rel_pr, 2)`が`size(weights, 2)`より大きい場合、`rel_pr`の最後の`size(weights, 2)`列が使用されます。


# 戻り値

  * `all_sn::Vector{T}`: 投資期間中の累積資産。
