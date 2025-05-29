```
TrackerResult
```

パスを[`Tracker`](@ref)で追跡した結果を含みます。

## フィールド

  * `return_code::Symbol`: 追跡が成功したかどうかを示すコード（`:success`）。すべての可能な値については[`TrackerCode`](@ref)を参照してください。
  * `solution::V`: 追跡が停止したときの解。
  * `t::ComplexF64`: 追跡が停止したときの`t`の値。
  * `accuracy::Float64`: `solution`の相対精度の推定値。
  * `accepted_steps::Int`: 受け入れられたステップの数。
  * `rejected_steps::Int`: 拒否されたステップの数。
  * `extended_precision::Bool`: `solution`の精度を達成するために拡張精度が必要かどうかを示します。
  * `extended_precision_used::Bool`: 追跡中に拡張精度が使用された場合は`true`です。
