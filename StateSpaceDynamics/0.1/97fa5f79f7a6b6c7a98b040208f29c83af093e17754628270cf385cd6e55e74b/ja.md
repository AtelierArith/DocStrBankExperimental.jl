```
HiddenMarkovModel
```

カスタムエミッションを持つ隠れマルコフモデル（HMM）。

# フィールド

  * `K::Int`: 状態の数。
  * `B::Vector=Vector()`: エミッションモデルのベクトル。
  * `emission=nothing`: Bがエミッションを欠いている場合、このモデルのクローンが残りを埋めるために使用されます。
  * `A::Matrix{<:Real}`: 遷移行列。
  * `πₖ::Vector{Float64}`: 初期状態分布。
