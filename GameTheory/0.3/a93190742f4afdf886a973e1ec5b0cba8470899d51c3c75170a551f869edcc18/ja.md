```
random_mixed_actions([rng=GLOBAL_RNG], nums_actions)
```

ランダムな混合アクションのタプル（浮動小数点数のベクトル）を返します。

# 引数

  * `rng::AbstractRNG=GLOBAL_RNG`: 使用される乱数生成器。
  * `nums_actions::NTuple{N,Int}`: 各プレイヤーのアクション数のNタプル。

# 戻り値

  * `::NTuple{N,Vector{Float64}}`: ランダムな混合アクションのNタプル。
