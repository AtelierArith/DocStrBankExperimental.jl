```
    atkinson94(setting, iters, crit)
```

LMS法を使用して外れ値を見つけるためにAtkinson94アルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: 回帰設定オブジェクト。
  * `iters::Int`: ランダムサンプルの数。
  * `crit::Float64`: 残差の臨界値

# 説明

このアルゴリズムは、初期の基本的なサブセットをランダムに選択し、基本的なサブセットを拡大するために非常に堅牢な方法（例：`lms`）を実行します。前方探索の各イテレーションで、最良の目的値とパラメータ推定値が保存されます。これらの値は、外れ値の視覚的調査のためにAtkinsonの鍾乳石プロットにも使用されます。`atkinsonstalactiteplot`を参照してください。

# 出力

  * `["optimum_index"]`: 最小目的が得られるイテレーション番号
  * `["residuals_matrix"]`: 各イテレーションで得られた残差の行列
  * `["outliers"]`: 検出された外れ値のインデックスの配列
  * `["objective"]`: 最小目的値
  * `["coef"]`: 推定された回帰係数
  * `["crit"]`: ユーザーによって与えられた臨界値。

# 例

```julia-repl
julia> reg = createRegressionSetting(@formula(stackloss ~ airflow + watertemp + acidcond), stackloss)
julia> atkinson94(reg)
Dict{Any,Any} with 6 entries:
  "optimum_index"    => 10
  "residuals_matrix" => [0.0286208 0.0620609 … 0.0796249 0.0; 0.0397778 0.120547 … 0.118437 0.0397778; … ; 1.21133 1.80846 … 0.690327 4.14366; 1.61977 0.971592 … 0.616204 3.58098]
  "outliers"         => [1, 3, 4, 21]
  "objective"        => 0.799134
  "coef"             => [-38.3133, 0.745659, 0.432794, 0.0104587]
  "crit"             => 3.0

```

# 参考文献

Atkinson, Anthony C. "Fast very robust methods for the detection of multiple outliers." Journal of the American Statistical Association 89.428 (1994): 1329-1339.
