```
fit(::Type{KnnModel}, index::AbstractSearchIndex, ctx::AbstractContext, labels::CategoricalArray; k=3, weight=KnnUniformWeightKernel())
```

`index`によってインデックスされた例とそれに関連付けられた`labels`を持つ新しい`KnnModel`分類器を作成します。

# 引数:

  * `KnnModel`: フィットリクエストをディスパッチするための型
  * `index`: 検索構造 [`SimilaritySearch.jl`](@ref) を参照
  * `labels`: ラベルのカテゴリカル配列

# キーワード引数

  * `k`: 使用する近傍の数。
  * `weight`: 近傍の重み付けスキーム。
