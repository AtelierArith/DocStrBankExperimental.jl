```
egm(rel_pr::AbstractMatrix, model::EGMFramework, η::AbstractFloat=0.05)
```

指数勾配法（EGM）アルゴリズムを実行します。このフレームワークには、[`EGE`](@ref)、[`EGR`](@ref)、および[`EGA`](@ref)の3つのバリアントが含まれています。

# 引数

  * `rel_pr::AbstractMatrix`: 相対価格を含む `n_assets` 行 `n_periods` 列の行列。
  * `model::EGMFramework`: EGMフレームワーク。[`EGE`](@ref)、[`EGR`](@ref)または[`EGA`](@ref)を使用できます。
  * `η::AbstractFloat=0.05`: 学習率。

# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref)オブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "GOOG"];

julia> querry = [get_prices(ticker, startdt="2019-01-01", enddt="2019-01-12")["adjclose"] for ticker in tickers];

julia> prices = stack(querry) |> permutedims;

julia> rel_pr = prices[:, 2:end]./prices[:, 1:end-1]
3×7 Matrix{Float64}:
 0.900393  1.04269  0.997774  1.01906  1.01698   1.0032    0.990182
 0.963212  1.04651  1.00128   1.00725  1.0143    0.993574  0.992278
 0.971516  1.05379  0.997833  1.00738  0.998495  0.995971  0.987723

julia> # EGEバリアント
julia> variant = EGE(0.5)

julia> model = egm(rel_pr, variant);

julia> model.b
3×7 Matrix{Float64}:
 0.333333  0.33294   0.332704  0.332576  0.332576  0.332634  0.332711
 0.333333  0.333493  0.333564  0.333619  0.333614  0.333647  0.33363
 0.333333  0.333567  0.333732  0.333805  0.33381   0.333719  0.333659

julia> # EGRバリアント
julia> variant = EGR(0.)

julia> model = egm(rel_pr, variant);

julia> model.b
3×7 Matrix{Float64}:
 0.333333  0.348653  0.350187  0.350575  0.348072  0.345816  0.344006
 0.333333  0.327     0.327299  0.326573  0.327852  0.326546  0.327824
 0.333333  0.324347  0.322514  0.322853  0.324077  0.327638  0.328169

julia> # EGAバリアント
julia> variant = EGA(0.5, 0.)

julia> model = egm(rel_pr, variant);

julia> model.b
3×7 Matrix{Float64}:
 0.333333  0.349056  0.350429  0.350706  0.348071  0.345757  0.343929
 0.333333  0.326833  0.327223  0.326516  0.327857  0.326514  0.327842
 0.333333  0.324111  0.322348  0.322779  0.324072  0.327729  0.328229
```

# 参考文献

> [オンラインポートフォリオ選択のための指数勾配法（EGM）](https://doi.org/10.1016/j.eswa.2021.115889)

