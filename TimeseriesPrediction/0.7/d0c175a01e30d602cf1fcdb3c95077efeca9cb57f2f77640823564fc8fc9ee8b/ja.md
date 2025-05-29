```
localmodel_tsp(s, γ::Int, τ, p::Int; method, ntype, stepsize)
localmodel_tsp(s, p::Int; method, ntype, stepsize)
```

`p` ポイントの時系列予測を、ローカル加重モデリング [1] を使用して行います。この関数は常に `s` と同じ型のオブジェクトを返します。`s` は時系列（ベクトル）または `AbstractDataset`（軌道）であり、返されるデータは常に `s` の最終点を出発点として含みます。これは、返されるデータの長さが `p + 1` であることを意味します。

`(s, γ, τ)` が与えられた場合、最初に `s` に対して `(γ, τ)` で `reconstruct`（`DelayEmbeddings` から）を呼び出します。`s` のみが与えられた場合、再構築は行われません。

## キーワード引数

  * `method = AverageLocalModel(ω_unsafe)` : [`AbstractLocalModel`](@ref) のサブタイプ。
  * `ntype = FixedMassNeighborhood(2)` : `AbstractNeighborhood`（`DelayEmbeddings` から）のサブタイプ。
  * `stepsize = 1` : 予測ステップサイズ。

## 説明

クエリポイントが与えられると、関数は近傍 `ntype` を使用してその近隣を見つけます。次に、近隣 `xnn` とその画像 `ynn` を使用して、提供された `method` を使用してクエリポイントの未来を予測します。画像 `ynn` は、未来に `stepsize` だけシフトされたポイント `xnn` です。

アルゴリズムは、長さ `p` の予測が作成されるまで反復的に適用され、クエリポイントは時系列の最後のポイントとして開始されます。

## 参考文献

[1] : D. Engster & U. Parlitz, *Handbook of Time Series Analysis* Ch. 1, VCH-Wiley (2006) ```
