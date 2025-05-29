```
ストリート
```

2つの[`Junction`](@ref)の間にエッジを保存します。

# フィールド

  * `endpointA::Int`: 最初のジャンクションのインデックス
  * `endpointB::Int`: 2番目のジャンクションのインデックス
  * `bidirectional::Bool`: `B -> A`が許可されているかどうか
  * `duration::Int`: ストリートを通過する際の時間コスト（秒単位）
  * `distance::Int`: ストリートの長さ（メートル単位）
