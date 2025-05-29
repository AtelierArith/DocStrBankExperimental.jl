```
sn(weights::AbstractMatrix{T}, rel_pr::AbstractMatrix{T}; init_inv::T=1.) where T<:AbstractFloat
```

Calculate the cumulative wealth of the portfolio during a period of time. Also, see [`mer`](@ref), [`ann_std`](@ref), [`apy`](@ref), [`ann_sharpe`](@ref), [`mdd`](@ref), [`calmar`](@ref), and [`opsmetrics`](@ref).

The formula for calculating the cumulative wealth of the portfolio is as follows:

$$
{S_n} = {S_0}\prod\limits_{t = 1}^T {\left\langle {{b_t},{x_t}} \right\rangle }
$$

where $S_0$ is the initial budget, $n$ is the investment horizon, $b_t$ is the vector of weights of the period $t$, and $x_t$ is the relative price of the $t$-th period.

# Arguments

  * `weights::AbstractMatrix{T}`: the weights of the portfolio.
  * `rel_pr::AbstractMatrix{T}`: the relative price of the stocks.

## Keyword Arguments

  * `init_inv::T=1`: the initial investment.

!!! warning "Beware!"
    The size of `weights` and `rel_pr` must be `(n_stocks, n_periods)`.


!!! note
    If `size(rel_pr, 2)` is greater than `size(weights, 2)`, then the last `size(weights, 2)` columns of `rel_pr` will be used.


# Returns

  * `all_sn::Vector{T}`: the cumulative wealth of investment during the investment period.
