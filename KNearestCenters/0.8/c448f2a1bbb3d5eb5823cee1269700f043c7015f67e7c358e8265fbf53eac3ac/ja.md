```
fit(::Type{KnnModel}, index::AbstractSearchIndex, meta::AbstractVecOrMat{<:Real}; k=3, weight=KnnUniformWeightKernel(), prediction=KnnSoftmaxPrediction())
fit(::Type{KnnModel}, examples::AbstractMatrix, meta::AbstractVecOrMat{<:Real}; k=3, weight=KnnUniformWeightKernel(), prediction=KnnSoftmaxPrediction(), dist=L2Distance())
```

新しい `KnnModel` 分類器を作成し、`index` によってインデックスされた例とそれに関連する `labels` を持ちます。

# 引数:

  * `KnnModel`: フィットリクエストをディスパッチするための型
  * `index`: 検索構造 [`SimilaritySearch.jl`](@ref) を参照
  * `examples`: [`SimilaritySearch.jl`](@ref) を使用してインデックスされる行列
  * `meta`: 数値的に関連するデータ

# キーワード引数

  * `k`: 使用される近傍の数。
  * `weight`: 近傍の重み付けスキーム。
  * `dist`: 使用される距離関数。
