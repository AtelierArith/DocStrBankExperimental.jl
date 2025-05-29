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

ガウス加重逆転（GWR）戦略を実行します。

!!! warning "注意!"
    `prices` は `n_assets` × `n_periods` のサイズの行列である必要があります。


# 方法 1

'GWR' バリアントを実行します。

## 引数

  * `prices::AbstractMatrix`: 価格の行列。
  * `horizon::Integer`: 投資のホライズン。
  * `τ::Real=2.8`: ガウス関数のパラメータ。
  * `𝛿::Integer=50`: ハイパーパラメータ。
  * `ϵ::AbstractFloat=0.005`: 加重範囲を制御するためのパラメータ。

## 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) オブジェクト。

## 例

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

# 方法 2

'GWR-A' バリアントを実行します。

## 引数

  * `prices::AbstractMatrix`: 価格の行列。
  * `horizon::Integer`: 投資のホライズン。
  * `τ::AbstractVector{<:Real}`: ガウス関数のパラメータ。
  * `𝛿::Integer=50`: ハイパーパラメータ。
  * `ϵ::AbstractFloat=0.005`: 加重範囲を制御するためのパラメータ。

## 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) オブジェクト。

## 例

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

# 参考

> [Gaussian Weighting Reversion Strategy for Accurate On-line Portfolio Selection](https://doi.org/10.1109/TSP.2019.2941067)

