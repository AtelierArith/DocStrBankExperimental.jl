```
localmodel_cp(source_pool, target_pool, source_pred, γ, τ; kwargs...)
```

*source* から *target* へのクロス予測を行います。ローカル加重モデリング [1] を使用します。`source_pred` は予測の入力であり、`source_pool` と `target_pool` は予測のためのプール/トレーニングデータとして使用されます。この関数は常に `target_pool` と同じ型のオブジェクトを返します。これは、時系列（ベクトル）または `AbstractDataset`（軌道）である可能性があります。

## キーワード引数

  * `method = AverageLocalModel(ω_unsafe)` : [`AbstractLocalModel`](@ref) のサブタイプ。
  * `ntype = FixedMassNeighborhood(2)` : `AbstractNeighborhood` のサブタイプ（`DelayEmbeddings` から）。
  * `stepsize = 1` : 予測ステップサイズ。

再構成のために `γ` と `τ` を渡す代わりに、既存の `Dataset` を `source_pool` と `source_pred` として渡すこともできます。この場合、再構成プロセスで導入されたインデックスシフトを考慮するために、追加のキーワード引数 `y_idx_shift::Int=0` が必要になる場合があります。

## 説明

クエリポイントが与えられると、関数は近傍 `ntype` を使用してその近傍を見つけます。次に、近傍 `xnn` とその画像 `ynn` を使用して、提供された `method` を使用してクエリポイントの画像の予測を行います。

## 参考文献

[1] : D. Engster & U. Parlitz, *Handbook of Time Series Analysis* Ch. 1, VCH-Wiley (2006)
