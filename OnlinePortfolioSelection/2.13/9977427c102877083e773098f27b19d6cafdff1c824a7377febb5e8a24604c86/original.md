```
sspo(
  p::AbstractMatrix,
  horizon::Integer,
  w::Integer,
  b̂ₜ::Union{Nothing, AbstractVector}=nothing,
  η::AbstractFloat=0.005,
  γ::AbstractFloat=0.01,
  λ::AbstractFloat=0.5,
  ζ::Integer=500,
  ϵ::AbstractFloat=1e-4,
  max_iter=1e4
)
```

Run Short-term Sparse Portfolio Optimization (SSPO) algorithm.

# Arguments

  * `p::AbstractMatrix`: Prices of the assets.
  * `horizon::Integer`: Number of investment periods.
  * `w::Integer`: Window size.
  * `b̂ₜ::Union{Nothing, AbstractVector}=nothing`: Initial portfolio weights. If `nothing` is passed, then a uniform portfolio will be selected for the first period.
  * `η::AbstractFloat=0.005`: Learning rate.
  * `γ::AbstractFloat=0.01`: Regularization parameter.
  * `λ::AbstractFloat=0.5`: Regularization parameter.
  * `ζ::Integer=500`: Regularization parameter.
  * `ϵ::AbstractFloat=1e-4`: Tolerance for the convergence of the algorithm.
  * `max_iter=1e4`: Maximum number of iterations.

# Returns

  * `::OPSAlgorithm`: An [`OPSAlgorithm`](@ref) object.

# Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["GOOG", "AAPL", "MSFT", "AMZN"]

julia> querry = [get_prices(ticker, startdt="2020-01-01", enddt="2020-01-31")["adjclose"] for ticker=tickers]

julia> prices = stack(querry, dims=1)

julia> h = 5

julia> w = 5

julia> model = sspo(prices, h, w);

julia> model.b
4×5 Matrix{Float64}:
 0.25  9.92018e-9  1.0         1.0  1.0
 0.25  0.0         0.0         0.0  0.0
 0.25  0.0         0.0         0.0  0.0
 0.25  1.0         9.94367e-9  0.0  0.0
```

# Reference

> [Short-term Sparse Portfolio Optimization Based on Alternating Direction Method of Multipliers](http://jmlr.org/papers/v19/17-558.html)

