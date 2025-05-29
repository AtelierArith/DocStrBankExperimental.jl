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

Calculate the metrics of an OPS algorithm. Also, see [`sn`](@ref), [`mer`](@ref), [`ir`](@ref), [`ann_std`](@ref), [`apy`](@ref), [`ann_sharpe`](@ref), [`mdd`](@ref), and [`calmar`](@ref).

# Arguments

  * `weights::AbstractMatrix{T}`: the weights of the portfolio.
  * `rel_pr::AbstractMatrix{T}`: the relative price of the stocks.
  * `rel_pr_market::AbstractVector{T}`: the relative price of the market.

## Keyword Arguments

  * `init_inv::T=1`: the initial investment.
  * `Rf::T=0.02`: the risk-free rate of return.
  * `dpy::S=252`: the number of days in a year.
  * `v::T=0.`: the transaction cost rate.

!!! warning
    The size of `weights` and `rel_pr` must be `(n_stocks, n_periods)`.


!!! note
    If `size(rel_pr, 2)` is greater than `size(weights, 2)`, then the last `size(weights, 2)` columns of `rel_pr` will be used.


# Returns

  * `::OPSMetrics`: An [`OPSMetrics`](@ref) object.
