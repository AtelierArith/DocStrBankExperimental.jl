```
random_pure_actions([rng=GLOBAL_RNG], nums_actions)
```

ランダムな純粋なアクション（整数）のタプルを返します。

# 引数

  * `rng::AbstractRNG=GLOBAL_RNG`: 使用される乱数生成器。
  * `nums_actions::NTuple{N,Int}`: 各プレイヤーのためのアクションの数のNタプル。

# 戻り値

  * `::NTuple{N,Int}`: ランダムな純粋なアクションのNタプル。
