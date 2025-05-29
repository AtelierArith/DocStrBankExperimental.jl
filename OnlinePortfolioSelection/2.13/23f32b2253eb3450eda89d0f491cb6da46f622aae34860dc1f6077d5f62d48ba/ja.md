```
cwmr(
  rel_pr::AbstractMatrix,
  ϕ::AbstractFloat,
  ϵ::AbstractFloat,
  variant::Type{<:CWMRVariant},
  ptfdis::Type{<:PtfDisVariant}
)

cwmr(
  rel_pr::AbstractMatrix,
  ϕ::AbstractVector,
  ϵ::AbstractVector,
  variant::Type{<:CWMRVariant},
  ptfdis::Type{<:PtfDisVariant};
  adt_ptf::Union{Nothing, AbstractVector{<:AbstractMatrix}}=nothing
)
```

Confidence Weighted Mean Reversion (CWMR)アルゴリズムを実行します。

!!! note "重要な注意"
    この関数を使用するには、最初に[Distributions.jl](https://github.com/JuliaStats/Distributions.jl)パッケージをインストールし、その後OnlinePortfolioSelection.jlパッケージと共にインポートする必要があります：

    ```julia
    julia> using Pkg; Pkg.add("Distributions")
    julia> using Distributions, OnlinePortfolioSelection
    ```


# メソッド

  * `cwmr(rel_pr::AbstractMatrix, ϕ::AbstractFloat, ϵ::AbstractFloat, variant::Type{<:CWMRVariant}, ptfdis::Type{<:PtfDisVariant})`
  * `cwmr(rel_pr::AbstractMatrix, ϕ::AbstractVector, ϵ::AbstractVector, variant::Type{<:CWMRVariant}, ptfdis::Type{<:PtfDisVariant}; adt_ptf::Union{Nothing, AbstractVector{<:AbstractMatrix}}=nothing)`

# メソッド 1

このメソッドを通じて、次のCWMRアルゴリズムのバリアントを実行できます：`CWMR-Var`、`CWMR-Stdev`、`CWMR-Var-s`および`CWMR-Stdev-s`。

## 引数

  * `rel_pr::AbstractMatrix`: 資産の相対価格。
  * `ϕ::AbstractFloat`: 学習率。
  * `ϵ::AbstractFloat`: 専門家の重み。これは∈ [0, 1]である必要があります。
  * `variant::Type{<:CWMRVariant}`: アルゴリズムのバリアント。`CWMRD`または`CWMRS`のいずれかです。
  * `ptfdis::Type{<:PtfDisVariant}`: ポートフォリオ分布。`Var`または`Stdev`のいずれかです。

!!! warning "注意!"
    `rel_pr`はサイズ`n_assets` × `n_periods`の行列である必要があります。


## 戻り値

  * `::OPSAlgorithm`: アルゴリズムの実行結果を含む[`OPSAlgorithm`](@ref)オブジェクト。

## 例

最初のメソッドのすべてのバリアント、例えば`CWMR-Var`、`CWMR-Stdev`、`CWMR-Var-s`および`CWMR-Stdev-s`を実行してみましょう：

```julia
julia> using OnlinePortfolioSelection, YFinance, Distributions

julia> tickers = ["AAPL", "MSFT", "AMZN"];

julia> startdt, enddt = "2019-01-01", "2019-01-10";

julia> querry = [get_prices(ticker, startdt=startdt, enddt=enddt)["adjclose"] for ticker=tickers];

julia> prices = stack(querry) |> permutedims;

julia> rel_pr = prices[:, 2:end]./prices[:, 1:end-1];

julia> variant, ptf_distrib = CWMRS, Var;

julia> model = cwmr(rel_pr, 0.5, 0.1, variant, ptf_distrib);

julia> model.b
3×5 Matrix{Float64}:
 0.344307  1.0         1.0         0.965464   0.0
 0.274593  2.76907e-8  0.0         0.0186898  1.0
 0.3811    2.73722e-8  2.23057e-9  0.0158464  2.21487e-7
```

# メソッド 2

このメソッドを通じて、次のCWMRアルゴリズムのバリアントを実行できます：`CWMR-Var-Mix`、`CWMR-Stdev-Mix`、`CWMR-Var-s-Mix`および`CWMR-Stdev-s-Mix`。

## 引数

  * `rel_pr::AbstractMatrix`: 資産の相対価格。
  * `ϕ::AbstractVector`: 学習率のベクトル。
  * `ϵ::AbstractVector`: 専門家の重みのベクトル。各要素は∈ [0, 1]である必要があります。
  * `variant::Type{<:CWMRVariant}`: アルゴリズムのバリアント。`CWMRD`または`CWMRS`のいずれかです。
  * `ptfdis::Type{<:PtfDisVariant}`: ポートフォリオ分布。`Var`または`Stdev`のいずれかです。

!!! warning "注意!"
    `rel_pr`はサイズ`n_assets` × `n_periods`の行列である必要があります。


## キーワード引数

  * `adt_ptf::Union{Nothing, AbstractVector{<:AbstractMatrix}}=nothing`: 追加の専門家ポートフォリオのベクトル。

!!! warning "注意!"
    `adt_ptf`は`nothing`またはサイズ`n_assets` × `n_periods`の行列のベクトルである可能性があります。論文に記載されているように、追加の専門家ポートフォリオは、'UP'、'EG'、'ONS'などの普遍的戦略のセットから選択する必要があります。詳細については、[`eg`](@ref)および[`up`](@ref)を参照してください。


## 戻り値

  * `::OPSAlgorithm`: アルゴリズムの実行結果を含む[`OPSAlgorithm`](@ref)オブジェクト。

## 例

第二のメソッドのすべてのバリアント、例えば`CWMR-Var-Mix`、`CWMR-Stdev-Mix`、`CWMR-Var-s-Mix`および`CWMR-Stdev-s-Mix`を実行してみましょう：

```julia
julia> variant, ptf_distrib = CWMRS, Var;

julia> model = cwmr(rel_pr, [0.5, 0.5], [0.1, 0.1], variant, ptf_distrib);

julia> model.b
3×5 Matrix{Float64}:
 0.329642  0.853456   0.863553   0.819096  0.0671245
 0.338512  0.0667117  0.0694979  0.102701  0.842985
 0.331846  0.0798325  0.0669491  0.078203  0.0898904
```

次に、2つの異なる'EG'ポートフォリオを追加の専門家ポートフォリオとして渡してみましょう：

```julia
julia> variant, ptf_distrib = CWMRS, Var;

julia> eg1 = eg(rel_pr, eta=0.1).b;

julia> eg2 = eg(rel_pr, eta=0.2).b;

julia> model = cwmr(rel_pr, [0.5, 0.5], [0.1, 0.1], variant, ptf_distrib, adt_ptf=[eg1, eg2]);

julia> model.b
3×5 Matrix{Float64}:
 0.318927  0.768507  0.721524  0.753618  0.135071
 0.338759  0.111292  0.16003   0.133229  0.741106
 0.342314  0.120201  0.118446  0.113154  0.123823
```

詳細情報と例については、[Confidence Weighted Mean Reversion (CWMR)](@ref)を参照してください。

# 参考文献

> [Confidence Weighted Mean Reversion Strategy for Online Portfolio Selection](http://dx.doi.org/10.1145/2435209.2435213)


```
