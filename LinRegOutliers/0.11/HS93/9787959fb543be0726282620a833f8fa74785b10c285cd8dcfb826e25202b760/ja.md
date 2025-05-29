```
hs93(setting; alpha = 0.05, basicsubsetindices = nothing)
```

与えられた回帰設定に対して Hadi & Simonoff (1993) アルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つ RegressionSetting オブジェクト。
  * `alpha::Float64`: 帰無仮説を棄却する確率のオプション引数。
  * `basicsubsetindices::Array{Int, 1}`: 初期基本サブセット。デフォルトでは、アルゴリズムは初期のクリーンな観測値のセットを作成します。

# 説明

初期のクリーンな観測値のサブセットを選択して拡大することによって前方探索を実行し、スケール残差が閾値を超えるまで反復します。

# 出力

  * `["outliers"]`: 外れ値のインデックスの配列
  * `["t"]`: 閾値、具体的には Student-T 分布の計算された分位点
  * `["d"]`: 内部および外部のスケール残差。
  * `["betas"]: 推定された回帰係数のベクトル。
  * `["converged"]: アルゴリズムが収束したかどうかを示すブール値。

# 例

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> hs93(reg0001)
Dict{Any,Any} with 3 entries:
  "outliers" => [14, 15, 16, 17, 18, 19, 20, 21]
  "t"        => -3.59263
  "d"        => [2.04474, 1.14495, -0.0633255, 0.0632934, -0.354349, -0.766818, -1.06862, -1.47638, -0.7…
  "converged"=> true
```

# 参考文献

Hadi, Ali S., and Jeffrey S. Simonoff. "Procedures for the identification of  multiple outliers in linear models." Journal of the American Statistical  Association 88.424 (1993): 1264-1272.
