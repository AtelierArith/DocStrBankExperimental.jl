```
detectAnomalies(data::AbstractArray{tp, N}, P::PARAMS) where {tp, N}
detectAnomalies(data::AbstractArray{tp, N}, algorithms::Array{String,1} = ["REC", "KDE"]; mean = 0) where {tp, N}
```

パラメータオブジェクト `P` のタイプ PARAMS を用いて異常を検出します。事前にトレーニングデータで `getParameters()` を使用してパラメータ `P` をトレーニングしてください。詳細は `getParameters()` を参照してください。事前に `P` をトレーニングしなくても、いくつかのアルゴリズム（SVDD、KNFSTを除く）を指定して `detectAnomalies(data, algorithms)` を使用することも可能です。この場合、内部的に `P` を初期化するためにいくつかのデフォルトパラメータが使用されます。

# 例

```
julia> training_data = randn(100, 2); testing_data = randn(100, 2);
julia> # アルゴリズム "REC", "KDE", "T2" および "KNN_Gamma" の異常スコアを計算し、それらの分位数を求め、アンサンブルスコアを返します
julia> P = getParameters(["REC", "KDE", "T2", "KNN_Gamma"], training_data, quantiles = true, ensemble_method = "mean");
julia> detectAnomalies(testing_data, P)
```
