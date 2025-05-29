```
oldem(
  rel_pr::AbstractMatrix,
  horizon::S,
  w::S,
  L::S,
  s::S,
  σ::T,
  ξ::T,
  γ::T;
  bt::AbstractVector = ones(size(rel_pr, 1))/size(rel_pr, 1)
) where {S<:Integer, T<:AbstractFloat}
```

オンライン低次元アンサンブル法 (OLDEM) を実行します。

# 引数

  * `rel_pr::AbstractMatrix`: 資産の価格相対を含むサイズ `n_assets` × `T` の行列。
  * `horizon::S`: 投資の時間枠。
  * `w::S`: ウィンドウサイズ。
  * `L::S`: サブシステムの数。
  * `s::S`: 各サブシステムの資産数。
  * `σ::T`: カーネルバンド幅。
  * `ξ::T`: トレードオフパラメータ。
  * `γ::T`: トレードオフパラメータ。

## キーワード引数

  * `bt::AbstractVector`: 初期ポートフォリオの重みを含む長さ `n_assets` のベクトル。おそらく、初期ポートフォリオは等重みポートフォリオです。ただし、次の条件を満たす任意の他のポートフォリオ重みを使用することができます: $\sum_{i=1}^{n\_assets} b_{i} = 1$。
  * `progress::Bool=false`: 進捗バーを表示します。

!!! warning "注意!"
    `rel_pr` はサイズ `n_assets` × `n_periods` の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) 型のオブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["MSFT", "TSLA", "AAPL", "META", "MMM"];

julia> querry = [
         get_prices(ticker, startdt="2020-01-01", enddt="2020-01-15")["adjclose"]
         for ticker in tickers
       ];

julia> prices = stack(querry) |> permutedims;

julia> x = prices[:, 2:end]./prices[:, 1:end-1]
5×8 Matrix{Float64}:
 0.987548  1.00259  0.990882  1.01593  1.01249   0.995373  1.01202  0.992957
 1.02963   1.01925  1.0388    1.0492   0.978055  0.993373  1.09769  1.02488
 0.990278  1.00797  0.995297  1.01609  1.02124   1.00226   1.02136  0.986497
 0.994709  1.01883  1.00216   1.01014  1.01431   0.998901  1.01766  0.987157
 0.991389  1.00095  0.995969  1.01535  1.00316   0.995971  1.00249  1.00249

julia> σ = 0.025;
julia> w = 2;
julia> h = 4;
julia> L = 4;
julia> s = 3;

julia> model = oldem(x, h, w, L, s, σ, 0.002, 0.25);

julia> model.b
5×4 Matrix{Float64}:
 0.2  1.99964e-8  1.0         0.0
 0.2  1.0         0.0         0.0
 0.2  0.0         0.0         1.99964e-8
 0.2  0.0         0.0         1.0
 0.2  0.0         1.99964e-8  0.0
```

# 参考文献

> [オンラインポートフォリオ選択と予測的瞬時リスク評価](https://doi.org/10.1016/j.patcog.2023.109872)

