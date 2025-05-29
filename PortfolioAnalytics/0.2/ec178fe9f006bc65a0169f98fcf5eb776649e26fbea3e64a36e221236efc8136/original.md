```
value_at_risk(R::TSFrame, p::Number=0.95; method::String="historical")
```

Calculates `Value-at-Risk(VaR)` from `asset returns`. Output is a `NamedArray`.

# Arguments:

  * `R::TSFrame`: column(s) of TSFrame object of asset returns
  * `p::Number=0.95`: confidence level
  * `method::String="historical"`: method of VaR calculation, available methods; `"historical"` and `"parametric"`

# Example

```julia
julia> var_historical = value_at_risk(returns)
4-element Named Vector{Float64}
95% historical VaR  │
────────────────────┼───────────
TSLA                │  -0.132252
NFLX                │ -0.0653681
MSFT                │  -0.035206

julia> var_parametric = value_at_risk(returns, 0.90, method = "parametric")
4-element Named Vector{Float64}
90% parametric VaR  │
────────────────────┼───────────
TSLA                │  -0.148553
NFLX                │ -0.0708139
MSFT                │ -0.0407369
```
