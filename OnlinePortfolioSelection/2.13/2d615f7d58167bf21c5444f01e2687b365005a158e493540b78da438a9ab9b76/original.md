```
ann_std(cum_ret::AbstractVector{AbstractFloat}; dpy)
```

Calculate the Annualized Standard Deviation ($\sigma_p$) of portfolio. Also, see [`sn`](@ref), [`mer`](@ref), [`apy`](@ref), [`ann_sharpe`](@ref), [`mdd`](@ref), [`calmar`](@ref), and [`opsmetrics`](@ref).

# Arguments

  * `cum_ret::AbstractVector{AbstractFloat}`: the cumulative wealth of investment during the investment period.

## Keyword Arguments

  * `dpy`: the number of days in a year.

# Returns

  * `::AbstractFloat`: the Annualized Standard Deviation ($\sigma_p$) of portfolio.
