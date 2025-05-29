```julia
cpphase!(osc, indices, value)

```

振動パラメータ構造体のCP位相を設定します

# 引数

  * `osc::OscillationParameters`: 振動パラメータ
  * `indices::Pair{<:Integer, <:Integer}`: 質量差のインデックス
  * `value` 振動パラメータに適用されるべき値
