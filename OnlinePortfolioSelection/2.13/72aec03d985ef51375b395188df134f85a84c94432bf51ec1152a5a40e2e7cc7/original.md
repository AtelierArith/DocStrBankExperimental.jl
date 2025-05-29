```
calmar(APY::T, MDD::T) where T<:AbstractFloat
```

Calculate the Calmar Ratio of investment. Also, see [`sn`](@ref), [`mer`](@ref), [`ann_std`](@ref), [`apy`](@ref), [`ann_sharpe`](@ref), [`mdd`](@ref), and [`opsmetrics`](@ref).

# Arguments

  * `APY::T`: the APY of investment.
  * `MDD::T`: the MDD of investment.

# Returns

  * `::AbstractFloat`: the Calmar Ratio of investment.
