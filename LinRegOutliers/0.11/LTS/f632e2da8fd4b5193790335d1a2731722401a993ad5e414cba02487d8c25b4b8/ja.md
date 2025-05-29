```
lts(setting; iters = nothing, crit = 2.5, earlystop = true)
```

与えられた回帰設定に対してFast-LTS（最小トリム二乗）アルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。
  * `iters::Int`: イテレーションの数。
  * `crit::Float64`: 臨界値。
  * `earlystop::Bool`: 最良の目的がiters / 2イテレーションで変わらない場合に早期停止。

# 説明

このアルゴリズムは、最初のh個の順序付けられた二乗残差の合計を最小化する回帰パラメータの推定値を探索します。ここで、hはInt(floor((n + p + 1.0) / 2.0))です。具体的には、私たちの実装は、基本的なサブセットをサイズhのクリーンな観測のサブセットに拡大するために集中ステップを使用するFast-LTSアルゴリズムを使用します。

# 出力

  * `["betas"]`: 推定された回帰係数
  * `["S"]`: 回帰の標準誤差
  * `["hsubset"]`: サイズhのクリーンな観測の最良サブセット。
  * `["outliers"]`: 外れ値のインデックスの配列
  * `["scaled.residuals"]`: スケーリングされた残差の配列
  * `["objective"]`: LTS目的値。

# 例

```julia-repl
julia> reg = createRegressionSetting(@formula(calls ~ year), phones);
julia> lts(reg)
Dict{Any,Any} with 6 entries:
  "betas"            => [-56.5219, 1.16488]
  "S"                => 1.10918
  "hsubset"          => [11, 10, 5, 6, 23, 12, 13, 9, 24, 7, 3, 4, 8]
  "outliers"         => [14, 15, 16, 17, 18, 19, 20, 21]
  "scaled.residuals" => [2.41447, 1.63472, 0.584504, 0.61617, 0.197052, -0.222066, -0.551027, -0.970146, -0.397538, -0.185558  …  …
  "objective"        => 3.43133
```

# 参考文献

Rousseeuw, Peter J., and Katrien Van Driessen. "An algorithm for positive-breakdown  regression based on concentration steps." Data Analysis.  Springer, Berlin, Heidelberg, 2000. 335-346.
