```
gwr(
  prices::AbstractMatrix,
  horizon::Integer,
  τ::Real=2.8,
  𝛿::Integer=50,
  ϵ::AbstractFloat=0.005
)

gwr(
  prices::AbstractMatrix,
  horizon::Integer,
  τ::AbstractVector{<:Real},
  𝛿::Integer=50,
  ϵ::AbstractFloat=0.005
)
```

Run the Gaussian Weighting Reversion (GWR) Strategy.

!!! warning "Beware!"
    `prices` should be a matrix of size `n_assets` × `n_periods`.


# Method 1

Run 'GWR' variant.

## Arguments

  * `prices::AbstractMatrix`: Matrix of prices.
  * `horizon::Integer`: The investment horizon.
  * `τ::Real=2.8`: The parameter of gaussian function.
  * `𝛿::Integer=50`: Hyperparameter.
  * `ϵ::AbstractFloat=0.005`: A parameter to control the weighted range.

## Returns

  * `::OPSAlgorithm`: An [`OPSAlgorithm`](@ref) object.

## Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["MSFT", "GOOG", "META"];

julia> querry = [get_prices(ticker, startdt="2020-01-01", enddt="2020-01-23")["adjclose"] for ticker in tickers];

julia> prices = stack(querry, dims=1)
3×14 Matrix{Float64}:
 154.78    152.852  153.247   151.85   154.269  156.196   155.473   157.343   156.235  157.246  160.128  161.024   160.446  159.675
  68.3685   68.033   69.7105   69.667   70.216   70.9915   71.4865   71.9615   71.544   71.96    72.585   74.0195   74.22    74.2975
 209.78    208.67   212.6     213.06   215.22   218.3     218.06    221.91    219.06   221.15   221.77   222.14    221.44   221.32

julia> h = 3

julia> model = gwr(prices, h);

julia> model.b
3×3 Matrix{Float64}:
 0.333333  0.333333  1.4095e-11
 0.333333  0.333333  0.0
 0.333333  0.333333  1.0
```

# Method 2

Run 'GWR-A' variant.

## Arguments

  * `prices::AbstractMatrix`: Matrix of prices.
  * `horizon::Integer`: The investment horizon.
  * `τ::AbstractVector{<:Real}`: The parameters of gaussian function.
  * `𝛿::Integer=50`: Hyperparameter.
  * `ϵ::AbstractFloat=0.005`: A parameter to control the weighted range.

## Returns

  * `::OPSAlgorithm`: An [`OPSAlgorithm`](@ref) object.

## Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["MSFT", "GOOG", "META"];

julia> querry = [get_prices(ticker, startdt="2020-01-01", enddt="2020-01-23")["adjclose"] for ticker in tickers];

julia> prices = stack(querry, dims=1)
3×14 Matrix{Float64}:
 154.78    152.852  153.247   151.85   154.269  156.196   155.473   157.343   156.235  157.246  160.128  161.024   160.446  159.675
  68.3685   68.033   69.7105   69.667   70.216   70.9915   71.4865   71.9615   71.544   71.96    72.585   74.0195   74.22    74.2975
 209.78    208.67   212.6     213.06   215.22   218.3     218.06    221.91    219.06   221.15   221.77   222.14    221.44   221.32

julia> h = 3

julia> model = gwr(prices, h, [2, 3, 4]);

julia> model.b
3×3 Matrix{Float64}:
 0.333333  0.0  1.20769e-11
 0.333333  0.0  0.0
 0.333333  1.0  1.0
```

# Reference

> [Gaussian Weighting Reversion Strategy for Accurate On-line Portfolio Selection](https://doi.org/10.1109/TSP.2019.2941067)

