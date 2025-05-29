```
mer(
  weights::AbstractMatrix{T},
  rel_pr::AbstractMatrix{T},
  𝘷::T=0.
) where T<:AbstractFloat
```

Calculate the investments's Mean excess return (MER). Also, see [`sn`](@ref), [`ann_std`](@ref), [`apy`](@ref), [`ann_sharpe`](@ref), [`mdd`](@ref), [`calmar`](@ref), and [`opsmetrics`](@ref).

# Arguments

  * `weights::AbstractMatrix{T}`: the weights of the portfolio.
  * `rel_pr::AbstractMatrix{T}`: the relative price of the stocks.
  * `𝘷::T=0.`: the transaction cost rate.

!!! warning
    The size of `weights` and `rel_pr` must be `(n_stocks, n_periods)`.


!!! note
    If `size(rel_pr, 2)` is greater than `size(weights, 2)`, then the last `size(weights, 2)` columns of `rel_pr` will be used.


# Returns

  * `MER::AbstractFloat`: the investments's Mean excess return (MER).
