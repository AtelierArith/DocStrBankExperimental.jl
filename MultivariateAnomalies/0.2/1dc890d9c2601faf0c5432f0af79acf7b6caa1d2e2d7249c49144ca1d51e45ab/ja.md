```
getParameters(algorithms::Array{String,1} = ["REC", "KDE"], training_data::AbstractArray{tp, 2} = [NaN NaN])
```

`algorithms` といくつかの `training_data` を行列として与えると、PARAMS 型のオブジェクトを返します。

# 引数

  * `algorithms`: `["REC", "KDE", "KNN_Gamma", "KNN_Delta", "SVDD", "KNFST", "T2"]` のサブセット
  * `training_data`: アルゴリズムのトレーニング用データ / パラメータを取得するためのデータ。
  * `dist::String = "Euclidean"`
  * `sigma_quantile::Float64 = 0.5` (中央値): 距離行列の分位数で、カーネル行列の重み付けパラメータを計算するために使用されます（`algorithms = ["SVDD", "KNFST", "KDE"]`）
  * `varepsilon_quantile` = デフォルトで `sigma_quantile`: 再発数がカウントされるハイパーボールの半径を計算するための距離行列の分位数（`algorihtms = ["REC"]`）
  * `k_perc::Float64 = 0.05`: 最近傍の数を推定するための `training_data` の最初の次元の割合（`algorithms = ["KNN-Gamma", "KNN_Delta"]`）
  * `nu::Float64 = 0.2`: `algorithms = ["SVDD"]` のための外れ値の最大割合を使用します
  * `temp_excl::Int64 = 0`: k-最近傍の再発としてカウントされる隣接点を除外します（`algorithms = ["REC", "KNN-Gamma", "KNN_Delta"]`）
  * `ensemble_method = "None"`: 使用されるアルゴリズムのアンサンブルを計算します。可能な選択肢（`compute_ensemble()` で指定）は "mean", "median", "max" および "min" です。
  * `quantiles = false`: アルゴリズムの出力スコアを分位数に変換します。

# 例

```
julia> using MultivariateAnomalies
julia> training_data = randn(100, 2); testing_data = randn(100, 2);
julia> P = getParameters(["REC", "KDE", "SVDD"], training_data, quantiles = false);
julia> detectAnomalies(testing_data, P)
```
