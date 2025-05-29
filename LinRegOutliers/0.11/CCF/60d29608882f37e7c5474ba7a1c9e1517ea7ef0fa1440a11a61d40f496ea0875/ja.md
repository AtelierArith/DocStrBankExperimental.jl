```
ccf(setting; starting_lambdas = nothing)
```

与えられた回帰設定に対してクリップされた凸関数の符号付き勾配降下法を実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。
  * `starting_lambdas::AbstractVector{Float64}`: 符号付き勾配降下法で使用される重みパラメータの開始値。
  * `alpha::Float64`: 点が外れ値としてラベル付けされる損失（損失がα以上の点は外れ値と呼ばれます）。
  * `max_iter::Int64`: 符号付き勾配降下法を実行する最大反復回数。
  * `beta::Float64`: ステップサイズパラメータ。
  * `tol::Float64`: 収束が宣言される許容範囲。

# 出力

  * `["betas"]`: ロバスト回帰係数
  * `[""outliers"]`: 外れ値のインデックスの配列
  * `[""lambdas"]`: 各反復で推定されたラムダ係数
  * `[""residuals"]`: 回帰残差。

# 例

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> ccf(reg0001)
Dict{Any,Any} with 4 entries:
  "betas"     => [-63.4816, 1.30406]
  "outliers"  => [15, 16, 17, 18, 19, 20]
  "lambdas"   => [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0  …  2.77556e-17, 2.77556e-17, 0…
  "residuals" => [-2.67878, -1.67473, -0.37067, -0.266613, 0.337444, 0.941501, 1.44556, 2.04962, 1…

```

# 参考文献

Barratt, S., Angeris, G. & Boyd, S. Minimizing a sum of clipped convex functions. Optim Lett 14, 2443–2459 (2020). https://doi.org/10.1007/s11590-020-01565-4
