```
ann_sharpe(APY::T, Rf::T, sigma_prtf::T) where T<:AbstractFloat
```

Calculate the Annualized Sharpe Ratio of investment. Also, see [`sn`](@ref), [`mer`](@ref), [`ann_std`](@ref), [`apy`](@ref), [`mdd`](@ref), [`calmar`](@ref), and [`opsmetrics`](@ref).

# Arguments

  * `APY::T`: the APY of investment.
  * `Rf::T`: the risk-free rate of return.
  * `sigma_prtf::T`: the standard deviation of the portfolio $\sigma_p$.

# Returns

  * `::AbstractFloat`: the Annualized Sharpe Ratio of investment.
