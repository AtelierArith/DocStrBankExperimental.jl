```
apy(Sn::AbstractFloat, n_periods::S; dpy::S=252) where S<:Int
```

Calculate the Annual Percentage Yield (APY) of investment. Also, see [`sn`](@ref), [`mer`](@ref), [`ann_std`](@ref), [`ann_sharpe`](@ref), [`mdd`](@ref), [`calmar`](@ref), and [`opsmetrics`](@ref).

# Arguments

  * `Sn::AbstractFloat`: the cumulative wealth of investment.
  * `n_periods::S`: the number investment periods.
  * `dpy::S=252`: the number of days in a year.

# Returns

  * `::AbstractFloat`: the APY of investment.
