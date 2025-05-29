```
svd(data::DataMatrix; nsv=3, var=:copy, obs=:copy, kwargs...)
```

`data`の特異値分解（SVD）を、[Halko et al. "Finding structure with randomness: Probabilistic algorithms for constructing approximate matrix decompositions"]からのランダムサブスペースSVDアルゴリズムを使用して計算します。SVDは、データが中心化されていると仮定する主成分分析（PCA）を実行するためにしばしば使用されます。

  * `nsv` - 特異値の数。
  * `var` - `:copy`（ソース`var`のコピーを作成）または`:keep`（ソース`var`オブジェクトを共有）を指定できます。
  * `obs` - `:copy`（ソース`obs`のコピーを作成）または`:keep`（ソース`obs`オブジェクトを共有）を指定できます。

数値精度に関連する追加のkwargsは、`SingleCellProjections.implicitsvd`に渡されます。

参照: [`SingleCellProjections.implicitsvd`](@ref)
