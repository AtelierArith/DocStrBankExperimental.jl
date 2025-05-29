```
mdd(Sn::AbstractVector{T}) where T<:AbstractFloat
```

Calculate the Maximum Drawdown (MDD) of investment. Also, see [`sn`](@ref), [`mer`](@ref), [`ann_std`](@ref), [`apy`](@ref), [`ann_sharpe`](@ref), [`calmar`](@ref), and [`opsmetrics`](@ref).

# Arguments

  * `Sn::AbstractVector{T}`: the cumulative wealth of investment during the investment period. see [`sn`](@ref).

# Returns

  * `::AbstractFloat`: the MDD of investment.
