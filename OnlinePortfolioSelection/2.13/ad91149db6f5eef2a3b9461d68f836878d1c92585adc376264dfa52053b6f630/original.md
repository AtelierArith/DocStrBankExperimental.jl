```
olmar(rel_pr::AbstractMatrix, horizon::Int, ω::Int, ϵ::Int)
olmar(rel_pr::AbstractMatrix, horizon::Int, ω::AbstractVector{<:Int}, ϵ::Int)
```

# Method 1

Run the Online Moving Average Reversion algorithm (OLMAR).

## Arguments

  * `rel_pr::AbstractMatrix`: Matrix of relative prices.
  * `horizon::Int`: Investment horizon.
  * `ω::Int`: Window size.
  * `ϵ::Int`: Reversion threshold.

!!! warning "Beware!"
    `rel_pr` should be a matrix of size `n_assets` × `n_periods`.


## Returns

  * `::OPSAlgorithm`: An [`OPSAlgorithm`](@ref) object.

## Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "AMZN", "GOOG", "META"];

julia> startdt, enddt = "2019-01-01", "2020-01-01"

julia> querry = [get_prices(ticker, startdt=startdt, enddt=enddt)["adjclose"] for ticker in tickers];

julia> prices = stack(querry) |> permutedims;

julia> rel_pr = prices[:, 2:end]./prices[:, 1:end-1];

julia> horizon = 5;
julia> windows = 3;
julia> epsilon = 4;

julia> m_olmar = olmar(rel_pr, horizon, windows, epsilon);

julia> m_olmar.b
5×5 Matrix{Float64}:
 0.2  1.0         0.484825  1.97835e-8  0.0
 0.2  1.95724e-8  0.515175  0.0         0.0
 0.2  0.0         0.0       1.0         1.0
 0.2  0.0         0.0       0.0         0.0
 0.2  0.0         0.0       0.0         1.9851e-8

julia> all(sum(m_olmar.b, dims=1) .≈ 1.0)
true
```

# Method 2

Run BAH(OLMAR) algorithm.

## Arguments

  * `rel_pr::AbstractMatrix`: Matrix of relative prices.
  * `horizon::Int`: Investment horizon.
  * `ω::AbstractVector{<:Int}`: Window sizes.
  * `ϵ::Int`: Reversion threshold.

!!! warning "Beware!"
    `rel_pr` should be a matrix of size `n_assets` × `n_periods`.


## Returns

  * `::OPSAlgorithm`: An [`OPSAlgorithm`](@ref) object.

## Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "AMZN", "GOOG", "META"];

julia> startdt, enddt = "2019-01-01", "2020-01-01"

julia> querry = [get_prices(ticker, startdt=startdt, enddt=enddt)["adjclose"] for ticker in tickers];

julia> prices = stack(querry) |> permutedims;

julia> rel_pr = prices[:, 2:end]./prices[:, 1:end-1];

julia> horizon = 5;
julia> windows = [3, 5, 7];
julia> epsilon = 4;

julia> model = olmar(rel_pr, horizon, windows, epsilon);

julia> model.b
5×5 Matrix{Float64}:
 0.2  0.2  0.333333    0.162297  1.33072e-8
 0.2  0.2  1.31177e-8  0.555158  0.0
 0.2  0.2  6.57906e-9  0.0       0.667358
 0.2  0.2  0.0         0.0       0.332642
 0.2  0.2  0.666667    0.282545  0.0
```

# References

> [On-Line Portfolio Selection with Moving Average Reversion](https://doi.org/10.48550/arXiv.1206.4626)

