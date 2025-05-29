```
BoundaryMovement(movement_function, is_moving; moving_particles=nothing)
```

# 引数

  * `movement_function`: $d$ 次元問題のための $d$ 次元の `SVector` を返す時間依存関数。
  * `is_moving`: 各タイムステップで粒子が動いているかどうかを判断する関数。そのブール値の返り値は、近傍探索が更新されるかどうかを決定するために必須です。

# キーワード引数

  * `moving_particles`: 動いている粒子のインデックス。デフォルトは [`BoundarySPHSystem`](@ref) の各粒子です。

以下の例では、`movement` は時間が `1.5` より小さい間、円を描いて動く粒子を表します。

# 例

```jldoctest; output = false
movement_function(t) = SVector(cos(2pi*t), sin(2pi*t))
is_moving(t) = t < 1.5

movement = BoundaryMovement(movement_function, is_moving)

# output
BoundaryMovement{typeof(movement_function), typeof(is_moving), Vector{Int64}}(movement_function, is_moving, Int64[])
```
