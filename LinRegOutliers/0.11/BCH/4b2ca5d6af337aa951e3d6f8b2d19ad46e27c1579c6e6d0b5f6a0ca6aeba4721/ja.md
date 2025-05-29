```
bch(setting; alpha = 0.05, maxiter = 1000, epsilon = 0.000001)
```

与えられた回帰設定に対して Billor & Chatterjee & Hadi (2006) アルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つ RegressionSetting オブジェクト。
  * `alpha::Float64`: 帰無仮説を棄却する確率のオプション引数。
  * `maxiter::Int`: 反復加重最小二乗推定を計算するための最大反復回数。
  * `epsilon::Float64`: 収束を決定するための精度。

# 説明

アルゴリズムは最初に基本的なサブセットを構築します。これらの基本的なサブセットは、反復的な最小二乗推定の初期重みを生成するために使用されます。この段階で得られた回帰係数はロバスト回帰推定値です。二乗正規化距離と二乗正規化残差は `bchplot` で使用され、外れ値とその特性の調査のための視覚的手段を提供します。

# 出力

  * `["betas"]`: 回帰係数の最終推定値
  * `["squared.normalized.robust.distances"]`:
  * `["weights"]`: WLS 推定の計算に使用される最終重み
  * `["outliers"]`: 外れ値のインデックスの配列
  * `["squared.normalized.residuals"]`: 二乗正規化残差の配列
  * `["residuals"]`: 回帰残差の配列
  * `["basic.subset"]`: 基本的なサブセットのインデックスの配列。

# 例

```julia-repl
julia> reg  = createRegressionSetting(@formula(calls ~ year), phones);
julia> Dict{Any,Any} with 7 entries:
"betas"                               => [-55.9205, 1.15572]
"squared.normalized.robust.distances" => [0.104671, 0.0865052, 0.0700692, 0.0553633, 0.0423875, 0.03…
"weights"                             => [0.00186158, 0.00952088, 0.0787321, 0.0787321, 0.0787321, 0…
"outliers"                            => [1, 14, 15, 16, 17, 18, 19, 20, 21]
"squared.normalized.residuals"        => [5.53742e-5, 2.42977e-5, 2.36066e-6, 2.77706e-6, 1.07985e-7…
"residuals"                           => [2.5348, 1.67908, 0.523367, 0.567651, 0.111936, -0.343779, …
"basic.subset"                        => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10  …  15, 16, 17, 18, 19, 20, …
```

# 参考文献

Billor, Nedret, Samprit Chatterjee, and Ali S. Hadi. "A re-weighted least squares method  for robust regression estimation." American journal of mathematical and management sciences 26.3-4 (2006): 229-252.
