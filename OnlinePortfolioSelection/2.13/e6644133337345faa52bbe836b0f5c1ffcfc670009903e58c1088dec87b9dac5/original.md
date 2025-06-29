```
pamr(rel_pr::AbstractMatrix, ϵ::AbstractFloat, C::AbstractFloat, model::PAMRModel)
```

Run the PAMR algorithm on the matrix of relative prices `rel_pr`.

# Arguments

  * `rel_pr::AbstractMatrix`: matrix of relative prices.
  * `ϵ::AbstractFloat`: Sensitivity parameter.
  * `C::AbstractFloat`: Aggressiveness parameter.
  * `model::PAMRModel`: PAMR model to use. All three variants, namely, `PAMR()`, `PAMR1()`, and `PAMR2()` are supported.

!!! warning "Beware!"
    `rel_price` should be a matrix of size `n_assets` × `n_periods`.


# Output

  * `::OPSAlgorithm`: An object of type [`OPSAlgorithm`](@ref).

# Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "AMZN", "META", "GOOG"]

julia> startdt, enddt = "2019-01-01", "2020-01-01"

julia> querry = [get_prices(ticker, startdt=startdt, enddt=enddt)["adjclose"] for ticker in tickers]

julia> prices = stack(querry) |> permutedims

julia> rel_pr =  prices[:, 2:end]./prices[:, 1:end-1]

julia> model = PAMR()

julia> eps = 0.01

julia> result = pamr(rel_pr, eps, model)

julia> result.b
5×251 Matrix{Float64}:
 0.2  0.224672  0.22704   0.230855  0.229743  …  0.0966823  0.0966057  0.0900667
 0.2  0.196884  0.197561  0.199825  0.203945     0.172787   0.171734   0.171626
 0.2  0.191777  0.190879  0.178504  0.178478     0.290126   0.289638   0.291135
 0.2  0.193456  0.193855  0.196363  0.189322     0.182514   0.181609   0.185527
 0.2  0.193211  0.190665  0.194453  0.198513     0.25789    0.260414   0.261645

julia> sum(result.b, dims=1) .|> isapprox(1.) |> all
true
```

In the same way, you can use `PAMR1()` and `PAMR2()`:

```julia
julia> model = PAMR1(C=0.02)

julia> eps = 0.01

julia> result = pamr(rel_pr, eps, model)

julia> result.b
5×251 Matrix{Float64}:
 0.2  0.200892  0.200978  0.201116  …  0.196264  0.19626   0.196257  0.19602
 0.2  0.199887  0.199912  0.199994     0.198835  0.199017  0.198979  0.198975
 0.2  0.199703  0.19967   0.199223     0.203659  0.203261  0.203243  0.203297
 0.2  0.199763  0.199778  0.199868     0.199246  0.199351  0.199319  0.19946
 0.2  0.199754  0.199662  0.199799     0.201997  0.20211   0.202202  0.202246

julia> model = PAMR2(C=1.)

julia> eps = 0.01

julia> result = pamr(rel_pr, eps, model)

julia> result.b
5×251 Matrix{Float64}:
 0.2  0.219093  0.220963  0.223948  …  0.119093  0.119013  0.118953  0.11385
 0.2  0.197589  0.198123  0.199895     0.175224  0.179199  0.178376  0.178291
 0.2  0.193636  0.192928  0.183242     0.279176  0.27052   0.270138  0.271307
 0.2  0.194936  0.19525   0.197214     0.183626  0.185922  0.185215  0.188272
 0.2  0.194746  0.192736  0.195701     0.242882  0.245346  0.247319  0.248279
```

# References

> [PAMR: Passive aggressive mean reversion strategy for portfolio selection](https://www.doi.org/10.1007/s10994-012-5281-z)

