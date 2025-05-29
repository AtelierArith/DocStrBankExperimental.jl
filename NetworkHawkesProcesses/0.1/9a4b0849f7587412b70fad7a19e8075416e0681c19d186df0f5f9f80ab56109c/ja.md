```
intensity(process::DiscreteHawkesProcess, convolved)
```

与えられた事前畳み込みイベントデータに基づいて、すべての時刻 `t ∈ [1, 2, ..., T]` における強度を計算します。

# 引数

  * `convolved::Array{Float64,3}`: 基底関数で畳み込まれたイベントカウントの `T x N x B` 配列。

# 戻り値

  * `λ::Array{Float64,2}`: 畳み込まれたイベントカウントに条件付けられた強度の `T x N` 配列。
