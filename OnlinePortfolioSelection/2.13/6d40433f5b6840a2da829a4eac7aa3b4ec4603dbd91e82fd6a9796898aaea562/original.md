```
cwogd(
  rel_pr::AbstractMatrix,
  γ::AbstractFloat,
  H;
  bj::AbstractMatrix=diagm(ones(size(rel_pr, 1)))
)
```

Run the CW-OGD algorithm.

# Positional Arguments

  * `rel_pr::AbstractMatrix`: Relative price matrix where it represents proportion of the closing price to the opening price of each asset in each day.
  * `γ::AbstractFloat`: Regular term coefficient of the basic expert's loss function.
  * `H::AbstractFloat`: Constant for calculating step sizes.

# Keyword Arguments

  * `bj::AbstractMatrix=diagm(ones(size(rel_pr, 1)))`: Matrix of experts opinions. Each column of this matrix must have just one positive element == 1. and others are zero. Also, sum of each column must be equal to 1. and number of rows must be equal to number of rows of `rel_pr`.

!!! warning "Beware!"
    `rel_pr` should be a matrix of size `n_assets` × `n_periods`.


# Returns

  * `::OPSAlgorithm`: An object of [`OPSAlgorithm`](@ref) type.

# Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "GOOG"];

julia> startdt, enddt = "2019-01-01", "2019-01-10";

julia> querry_open_price = [get_prices(ticker, startdt=startdt, enddt=enddt)["open"] for ticker in tickers];

julia> open_pr = reduce(hcat, querry_open_price) |> permutedims;

julia> querry_close_pr = [get_prices(ticker, startdt=startdt, enddt=enddt)["adjclose"] for ticker in tickers];

julia> close_pr = reduce(hcat, querry_close_pr) |> permutedims;

julia> rel_pr = close_pr ./ open_pr
3×6 Matrix{Float64}:
 1.01956  0.987568  1.02581  0.994822  1.00796   1.01335
 1.01577  0.973027  1.02216  1.00413   0.997671  1.00395
 1.0288   0.976042  1.03692  0.997097  1.00016   0.993538

julia> gamma = 0.1; H = 0.5;

julia> model = cwogd(rel_pr, gamma, H);

julia> model.b
3×5 Matrix{Float64}:
 0.333333  0.351048  0.346241  0.338507  0.350524
 0.333333  0.321382  0.309454  0.320351  0.311853
 0.333333  0.32757   0.344305  0.341142  0.337623

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

Or using a custom matrix of experts opinions:

```julia
julia> b1 = [
          0.0 1.0 0.0
          1.0 0.0 0.0
          0.0 0.0 1.0
        ]

julia> model = cwogd(rel_pr, gamma, H, bj=b1);

julia> model.b
3×6 Matrix{Float64}:
 0.333333  0.329802  0.347517  0.34271   0.334976  0.346992
 0.333333  0.322351  0.3104    0.298472  0.309369  0.300871
 0.333333  0.347847  0.342083  0.358819  0.355655  0.352137

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

# References

> [[1] Combining expert weights for online portfolio selection based on the gradient descent algorithm.](https://doi.org/10.1016/j.knosys.2021.107533)

