```
lta(setting; exact = false, earlystop = true)
```

与えられた回帰設定に対して、Hawkins & Olive (1999) アルゴリズム（最小トリム絶対偏差）を実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。
  * `exact::Bool`: 回帰パラメータの数pのすべての可能な部分集合を考慮するかどうか。
  * `earlystop::Bool`: 残りのイテレーション数 / 5 イテレーションで最良の目的が変わらない場合に早期停止。

# 説明

`lta`は、最初のh絶対残差の合計を最小化するトリムバージョンの`lad`であり、hはInt(floor((n + p + 1.0) / 2.0))です。

# 出力

  * `["betas"]`: 推定された回帰係数
  * `["objective]`: 目的値

# 例

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> lta(reg0001)
Dict{Any,Any} with 2 entries:
  "betas"     => [-55.5, 1.15]
  "objective" => 5.7

julia> lta(reg0001, exact = true)
Dict{Any,Any} with 2 entries:
  "betas"     => [-55.5, 1.15]
  "objective" => 5.7  
```

# 参考文献

Hawkins, Douglas M., and David Olive. "Applications and algorithms for least trimmed sum of  absolute deviations regression." Computational Statistics & Data Analysis 32.2 (1999): 119-134.
