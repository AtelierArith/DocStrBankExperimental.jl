```
fit(::Type{<:UMAP}, index_or_data;
    k=15,
    dist::SemiMetric=L2Distance,
    minbatch=0,
    kwargs...)
```

`fit`のラッパーで、`index_or_data`上で`n_nearests`最近傍を計算し、これらと`kwargs`を通常の`fit`に渡します。

# 引数

  * `index_or_data`: すでに構築されたインデックス（`SimilaritySearch`を参照）、行列、または抽象データベース（`SimilaritySearch`）

# キーワード引数

  * `k=15`: 計算する近傍の数
  * `dist=L2Distance()`: 距離関数（`Distances.jl`を参照）
  * `minbatch=0`: 並列計算の方法を制御します。ゼロは`SimilaritySearch`のデフォルトを使用し、-1は並列計算を回避します。`Polyester`パッケージの`@batch`マクロに渡されます。
