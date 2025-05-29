```
at(rel_pr::AbstractMatrix, b::AbstractMatrix)
```

Calculate the average turnover of the portfolio. Also, see [`sn`](@ref), [`mer`](@ref), [`ir`](@ref), [`ann_std`](@ref), [`apy`](@ref), [`ann_sharpe`](@ref), [`mdd`](@ref), and [`calmar`](@ref).

# Arguments

  * `rel_pr::AbstractMatrix`: The relative price of the stocks.
  * `b::AbstractMatrix`: The weights of the portfolio.

# Returns

  * `::AbstractFloat`: the average turnover of the portfolio.
