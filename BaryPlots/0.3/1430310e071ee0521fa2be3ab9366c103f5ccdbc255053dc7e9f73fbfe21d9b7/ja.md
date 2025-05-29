```
check_stability(x_eq::Vector{Float64}, params::ReplicatorParams; stability_tol::Float64 = 1e-6) -> Bool
```

平衡点の安定性を、縮小系のヤコビ行列の固有値を分析することによって決定します。

# 引数

  * `x_eq`: 平衡点での戦略頻度を表すベクトル。
  * `params`: 支払い関数と追加のパラメータを含む `ReplicatorParams` 構造体。
  * `stability_tol`: 固有値に基づいて安定性を決定するための許容誤差。

# 戻り値

  * 平衡が安定であれば `true`、そうでなければ `false`。

# 注意事項

  * 縮小系は単体制約（合計が1になる）により1つの変数を除外します。
  * 安定性は固有値の実部の符号によって決定されます。
