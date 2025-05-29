```
fuzzy_cmeans(data::AbstractMatrix, C::Integer, fuzziness::Real;
             [dist_metric::SemiMetric], [...]) -> FuzzyCMeansResult
```

与えられた `data` に対してファジーC平均クラスタリングを実行します。

# 引数

  * `data::AbstractMatrix`: $d×n$ データ行列。各列は1つの $d$ 次元データポイントを表します。
  * `C::Integer`: ファジークラスタの数、$2 ≤ C < n$。
  * `fuzziness::Real`: クラスタのファジネス ($μ$ は [数理的定式化](@ref fuzzy_cmeans_def) における)、$μ > 1$。

オプションのキーワード引数:

  * `dist_metric::SemiMetric` (デフォルトは `Euclidean`): データポイント間の距離を定義する `SemiMetric` オブジェクト
  * `maxiter`, `tol`, `display`, `rng`: [共通オプション](@ref common_options) を参照してください。
