```
cluslog(
  rel_pr::AbstractMatrix{<:AbstractFloat},
  horizon::Int,
  TW::Int,
  clus_mod::Type{<:ClusLogVariant},
  nclusters::Int,
  nclustering::Int,
  boundries::NTuple{2, AbstractFloat};
  progress::Bool=true
)
```

与えられたデータに対してKMNLOG、KMDLOGなどのアルゴリズムを実行します。

!!! note "重要な注意"
    この関数を使用するには、まず[Clustering.jl](https://github.com/JuliaStats/Clustering.jl)パッケージをインストールし、その後OnlinePortfolioSelection.jlパッケージと一緒にインポートする必要があります：

    ```julia
    julia> using Pkg; Pkg.add(name="Clustering", version="0.15.2")
    julia> using OnlinePortfolioSelection, Clustering
    ```


# 引数

  * `rel_pr::AbstractMatrix{<:AbstractFloat}`: 資産の相対価格。各列は特定の時点での資産の価格を表します。
  * `horizon::Int`: 取引日数。
  * `TW::Int`: 検討する最大時間ウィンドウの長さ。
  * `clus_mod::Type{<:ClusLogVariant}`: 使用するクラスタリングモデル。現在、[`KMNLOG`](@ref)と[`KMDLOG`](@ref)のみがサポートされています。
  * `nclusters::Int`: 検討する最大クラスタ数。
  * `nclustering::Int`: 最適なクラスタ数のためにクラスタリングアルゴリズムを実行する回数。
  * `boundries::NTuple{2, AbstractFloat}`: ポートフォリオ内の資産の重みの下限と上限。

# キーワード引数

  * `progress::Bool=true`: 進捗を記録するかどうか。

!!! warning "注意!"
    `rel_pr`はサイズ`n_assets` × `n_periods`の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref)オブジェクト。

# 例

現在利用可能なクラスタリングモデルは2つ：[`KMNLOG`](@ref)と[`KMDLOG`](@ref)です。最初の例は[`KMNLOG`](@ref)を利用しています：

```julia
julia> using OnlinePortfolioSelection, Clustering

julia> adj_close = [
         1.5464 1.5852 1.6532 1.7245 1.5251 1.4185 1.2156 1.3231 1.3585 1.4563 1.4456
         1.2411 1.2854 1.3456 1.4123 1.5212 1.5015 1.4913 1.5212 1.5015 1.4913 1.5015
         1.3212 1.3315 1.3213 1.3153 1.3031 1.2913 1.2950 1.2953 1.3315 1.3213 1.3315
       ]

julia> rel_pr = adj_close[:, 2:end]./adj_close[:, 1:end-1]

julia> horizon = 3; TW = 3; nclusters_ = 3; nclustering = 10; lb, ub = 0.0, 1.;

julia> model = cluslog(rel_pr, horizon, TW, KMNLOG, nclusters_, nclustering, (lb, ub));

julia> model.b
3×3 Matrix{Float64}:
0.00264911  0.00317815  0.148012
0.973581    0.971728    0.848037
0.02377     0.0250939   0.00395028

julia> sum(model.b , dims=1) .|> isapprox(1.) |> all
true
```

同じアプローチは[`KMDLOG`](@ref)にも適用できます：

```julia
julia> using OnlinePortfolioSelection, Clustering

julia> model = cluslog(rel_pr, horizon, TW, KMDLOG, nclusters_, nclustering, (lb, ub));

julia> model.b
3×3 Matrix{Float64}:
4.59938e-7  4.96421e-7  4.89426e-7
0.999998    0.999997    0.999997
2.02964e-6  2.02787e-6  2.02964e-6

julia> sum(model.b , dims=1) .|> isapprox(1.) |> all
true
```

さらに[`KMNLOG`](@ref)と[`KMDLOG`](@ref)も参照してください。

# 参考文献

> [取引コストを考慮したクラスタリングアプローチを用いたオンラインポートフォリオ選択アルゴリズム](https://doi.org/10.1016/j.eswa.2020.113546)


```
