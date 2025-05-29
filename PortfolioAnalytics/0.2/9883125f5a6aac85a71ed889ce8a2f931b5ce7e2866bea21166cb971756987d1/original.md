```
sharpe(R::TSFrame, Rf::Number=0)
```

Calculates `Sharpe Ratio` from `asset returns`. Output is a `NamedArray`.

# Arguments:

  * `R::TSFrame`: column(s) of TSFrame object of asset returns
  * `Rf::Number=0`: Risk-free rate

# Example

```julia
julia> sharpe = sharpe(returns)
4-element Named Vector{Float64}
Sharpe Ratio (Rf=0)  │
─────────────────────┼─────────
TSLA                 │ 0.288602
NFLX                 │ 0.170242
MSFT                 │ 0.606824
```
