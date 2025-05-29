```
estimate_ordinal_model_probabilities(df, table)
```

観測されたセルカウントに基づいて、順序ロジットモデルの確率を推定します。

# 引数

  * `df::DataFrame`: 予測変数を含むデータフレーム。
  * `table::AbstractMatrix`: 確率を推定するための予測値の行列。

# 戻り値

  * `prob::Vector{Float64}`: 推定された確率のベクトル。
