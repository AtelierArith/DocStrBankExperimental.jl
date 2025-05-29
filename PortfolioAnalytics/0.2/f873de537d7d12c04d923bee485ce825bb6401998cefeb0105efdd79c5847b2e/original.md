```
es(R::TSFrame, p::Number=0.95; method::String="historical")
```

Calculates `Expected Shortfall (Conditional Value at Risk)` from `asset returns`. Output is a `NamedArray`.

# Arguments:

  * `R::TSFrame`: column(s) of TSFrame object of asset returns
  * `p::Number=0.95`: confidence level
  * `method::String="historical"`: method of Expected Shortfall calculation

# Example

```julia
julia> ES = es(returns)
4-element Named Vector{Any}
95% historical ES  │
───────────────────┼───────────
TSLA               │  -0.148766
NFLX               │ -0.0701279
MSFT               │  -0.066119
```

# Notes:

  * Available methods: `"historical"` and `"parametric"`
  * Monte Carlo method will be implemented as part of the next release
