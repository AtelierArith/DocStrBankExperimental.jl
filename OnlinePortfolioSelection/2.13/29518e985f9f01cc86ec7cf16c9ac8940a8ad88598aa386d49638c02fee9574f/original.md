```
load(adj_close::AbstractMatrix{T}, α::T, ω::S, horizon::S, η::T, ϵ::T=1.5) where {T<:AbstractFloat, S<:Int}
```

Run LOAD algorithm.

# Arguments

  * `adj_close::AbstractMatrix{T}`: Adjusted close price data.
  * `α::T`: Decay factor. (0 < α < 1)
  * `ω::S`: Window size. (ω > 0)
  * `horizon::S`: Investment horizon. (n_periods > horizon > 0)
  * `η::T`: Threshold value. (η > 0)
  * `ϵ::T=1.5`: Expected return threshold value.

!!! warning "Beware!"
    `adj_close` should be a matrix of size `n_assets` × `n_periods`.


# Returns

  * `::OPSAlgorithm`: An object of type `OPSAlgorithm` containing the weights of each asset for each period.

# Example

```julia
# Get data
julia> using YFinance
julia> startdt, enddt = "2022-04-01", "2023-04-27";
julia> querry = [
          get_prices(ticker, startdt=startdt, enddt=enddt)["adjclose"] for ticker in tickers
       ];
julia> prices = reduce(hcat, querry);
julia> prices = permutedims(prices);

julia> using OnlinePortfolioSelection

julia> model = load(prices, 0.5, 30, 5, 0.1);

julia> model.b
5×5 Matrix{Float64}:
 0.2  2.85298e-8  0.0        0.0       0.0
 0.2  0.455053    0.637299   0.694061  0.653211
 0.2  0.215388    0.0581291  0.0       0.0
 0.2  0.329559    0.304572   0.305939  0.346789
 0.2  6.06128e-9  0.0        0.0       0.0

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

# References

> [A local adaptive learning system for online portfolio selection](https://doi.org/10.1016/j.knosys.2019.104958)

