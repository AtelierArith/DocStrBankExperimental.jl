```
generate(Q, n; dt=1, initial_condition=rand(1:size(Q)[1]))
```

長さ `n` のマルコフ連鎖を遷移行列 `Q` と時間ステップ `dt` で生成します。

# 引数

  * `Q::AbstractMatrix`: マルコフ連鎖の遷移行列または生成器。
  * `n::Int`: マルコフ連鎖の長さ。
  * `dt::Real=1`: マルコフ連鎖の時間ステップ。
  * `initial_condition::Int=rand(1:size(Q)[1])`: マルコフ連鎖の初期条件。

# キーワード引数

  * `progress::Bool=false`: 進行状況バーを表示するかどうか。

# 戻り値

  * `Vector{Int}`: 遷移行列 `Q` と時間ステップ `dt` によって生成された長さ `n` のマルコフ連鎖。
