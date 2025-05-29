```
portfolio_optimize(R::TSFrame, objective::String = "minumum variance"; target = Nothing, Rf::Number = 0)
```

Calculates the `optimal Portfolio weights` for a given `objective` and `target` return.

# Arguments:

  * `R::TSFrame`: columns of TSFrame object of asset returns
  * `objective::String = "minumum variance"`: portfolio objective, minimizes the standard deviation for the portfolio. Available objecives; `"minumum variance"` and `"maximum sharpe"`
  * `target = Nothing`: target portfolio mean return for a chosen objective. It allows to move accross the efficient frontier
  * `Rf::Number = 0`: risk-free rate, used with `maximum sharpe`

# Example

```julia
julia> opt1 = portfolio_optimize(returns, "minumum variance")
julia> opt_weights = opt1.pweights
3-element Named Vector{Float64}
Optimal Weights  │
─────────────────┼───────
TSLA             │   -0.0
NFLX             │ 0.4438
MSFT             │ 0.5562


# plotting efficient frontier and decision space
julia> opt1.plt
```

Optimize minumum-variance portfolio with a minumum return target of 4%

```julia
julia> opt2 = portfolio_optimize(returns, "minumum variance", target = 0.04)

# optimal portfolio weights for a chosen objective and target return
julia> opt2.pweights
3-element Named Vector{Float64}
Optimal Weights  │
─────────────────┼───────
TSLA             │ 0.5142
NFLX             │    0.0
MSFT             │ 0.4858
```

Optimization of maximum sharpe portfolio

```julia
julia> opt3 = portfolio_optimize(returns, "maximum sharpe")
julia> opt3.pweights
3-element Named Vector{Float64}
Optimal Weights  │
─────────────────┼─────
TSLA             │ -0.0
NFLX             │  0.0
MSFT             │  1.0

julia> opt3.plt
```

Optimization of maximum sharpe portfolio with target return of at least 4%

```julia
julia> opt4 = portfolio_optimize(returns, "maximum sharpe", target = 0.04)
julia> opt4.pweights
3-element Named Vector{Float64}
Optimal Weights  │
─────────────────┼───────
TSLA             │ 0.5142
NFLX             │   -0.0
MSFT             │ 0.4858
```

# Output:

Named Tuple

  * 1, `preturn` : portfolio mean return
  * 2, `prisk`: portfolio standard deviation
  * 3, `psharpe`: portfolio sharpe ratio
  * 4, `pweights`: optimal portfolio weights for chosen `objective` and defined `target`
  * 5, `plt`: plot of the `efficient frontier` and `decision space`
  * 6, `pm`: list of `expected returns` per each solution
  * 7, `po`: list of objective values per portfolio. If the objective is `minimum-variance`, then standard deviations of each optimal portfolio. If the objective is set to the `maximum-sharpe`, then the Sharpe Ratios of each portfolio.
  * 8, `pw`: list of `weights` per each solution
