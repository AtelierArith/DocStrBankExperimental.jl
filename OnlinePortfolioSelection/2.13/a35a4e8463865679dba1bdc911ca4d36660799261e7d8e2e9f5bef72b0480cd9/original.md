```
ir(
  weights::AbstractMatrix{S},
  rel_pr::AbstractMatrix{S},
  rel_pr_market::AbstractVector{S};
  init_inv::S=1.
) where S<:AbstractFloat
```

Calculate the Information Ratio (IR) of portfolio. Also, see [`sn`](@ref), [`mer`](@ref), [`ann_std`](@ref), [`apy`](@ref), [`ann_sharpe`](@ref), [`mdd`](@ref), [`calmar`](@ref), and [`opsmetrics`](@ref).

The formula for calculating the Information Ratio (IR) of portfolio is as follows:

$$
IR = \frac{{{{\bar R}_s} - {{\bar R}_m}}}{{\sigma \left( {{R_s} - {R_m}} \right)}}
$$

where $R_s$ represents the portfolio's daily return, $R_m$ represents the market's daily return, $\bar R_s$ represents the portfolio's average daily return, $\bar R_m$ represents the market's average daily return, and $\sigma$ represents the standard deviation of the portfolio's daily excess return over the market. Note that in this package, the logarithmic return is used.

# Arguments

  * `weights::AbstractMatrix{S}`: the weights of the portfolio.
  * `rel_pr::AbstractMatrix{S}`: the relative price of the stocks.
  * `rel_pr_market::AbstractVector{S}`: the relative price of the market.

## Keyword Arguments

  * `init_inv::S=1`: the initial investment.

!!! warning
    The size of `weights` and `rel_pr` must be `(n_stocks, n_periods)`.


!!! note
    If `size(rel_pr, 2)` is greater than `size(weights, 2)`, then the last `size(weights, 2)` columns of `rel_pr` will be used. The size of `rel_pr_market` will automatically be adjusted to the size of `w`.


# Returns

  * `::AbstractFloat`: the Information Ratio (IR) of portfolio for the investment period.

# References

> [Adaptive online portfolio strategy based on exponential gradient updates](https://doi.org/10.1007/s10878-021-00800-7)

