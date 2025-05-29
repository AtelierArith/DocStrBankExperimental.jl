```
kforecast(settings::KalmanSettings, X::Union{FloatVector, Nothing}, h::Int64)
```

`X`を`h`ステップ先まで予測します。

# 引数

  * `settings`: KalmanSettings構造体
  * `X`: 状態ベクトル
  * `h`: 予測ホライズン

    kforecast(settings::KalmanSettings, X::Union{FloatVector, Nothing}, P::Union{SymMatrix, Nothing}, h::Int64)

`X`と`P`を`h`ステップ先まで予測します。

# 引数

  * `settings`: KalmanSettings構造体
  * `X`: 状態ベクトル
  * `P`: 状態の共分散行列
  * `h`: 予測ホライズン
