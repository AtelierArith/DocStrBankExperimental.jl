```
mrvol(
  rel_pr::AbstractMatrix{T},
  rel_vol::AbstractMatrix{T},
  horizon::S,
  Wₘᵢₙ::S,
  Wₘₐₓ::S,
  λ::T,
  η::T
) where {T<:AbstractFloat, S<:Integer}
```

Run MRvol algorithm.

# Arguments

  * `rel_pr::AbstractMatrix{T}`: Relative price matrix where it represents proportion of the closing price to the opening price of each asset in each day.
  * `rel_vol::AbstractMatrix{T}`: Relative volume matrix where 𝘷ᵢⱼ represents the tᵗʰ trading volume of asset 𝑖 divided by the (t - 1)ᵗʰ trading volume of asset 𝑖.
  * `horizon::S`: Investment horizon. The last `horizon` days of the data will be used to run the algorithm.
  * `Wₘᵢₙ::S`: Minimum window size.
  * `Wₘₐₓ::S`: Maximum window size.
  * `λ::T`: Trade-off parameter in the loss function.
  * `η::T`: Learning rate.

!!! warning "Beware!"
    `rel_pr` and `rel_vol` should be matrixes of size `n_assets` × `n_periods`.


# Returns

  * `::OPSAlgorithm`: An [`OPSAlgorithm`](@ref) object.

# Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "GOOG"];

julia> startdt, enddt = "2019-01-01", "2020-01-01";

julia> querry_open_price = [get_prices(ticker, startdt=startdt, enddt=enddt)["open"] for ticker in tickers];

julia> open_pr = reduce(hcat, querry_open_price) |> permutedims;

julia> querry_close_pr = [get_prices(ticker, startdt=startdt, enddt=enddt)["adjclose"] for ticker in tickers];

julia> close_pr = reduce(hcat, querry_close_pr) |> permutedims;

julia> querry_vol = [get_prices(ticker, startdt=startdt, enddt=enddt)["vol"] for ticker in tickers];

julia> vol = reduce(hcat, querry_vol) |> permutedims;

julia> rel_pr = (close_pr ./ open_pr)[:, 2:end];

julia> rel_vol = vol[:, 2:end] ./ vol[:, 1:end-1];

julia> size(rel_pr) == size(rel_vol)
true

julia> horizon = 100; Wₘᵢₙ = 4; Wₘₐₓ = 10; λ = 0.05; η = 0.01;

julia> r = mrvol(rel_pr, rel_vol, horizon, Wₘᵢₙ, Wₘₐₓ, λ, η);

julia> r.b
3×100 Matrix{Float64}:
 0.333333  0.0204062  0.0444759  …  0.38213   0.467793
 0.333333  0.359864   0.194139      0.213264  0.281519
 0.333333  0.61973    0.761385      0.404606  0.250689
```

# References

> [Online portfolio selection of integrating expert strategies based on mean reversion and trading volume.](https://doi.org/10.1016/j.eswa.2023.121472)

