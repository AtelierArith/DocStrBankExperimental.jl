```
BoundarySPHSystem(initial_condition, boundary_model; movement=nothing, adhesion_coefficient=0.0)
```

境界粒子によってモデル化された境界のシステム。流体と境界粒子の相互作用は境界モデルによって指定されます。

# 引数

  * `initial_condition`: 初期条件 (see [`InitialCondition`](@ref))
  * `boundary_model`: 境界モデル (see [Boundary Models](@ref boundary_models))

# キーワード引数

  * `movement`: 移動する境界の場合、[`BoundaryMovement`](@ref)を渡すことができます。
  * `adhesion_coefficient`: 流体が表面に付着することを指定する係数。注意: 現在、すべての流体が同じ付着係数を持つと仮定されています。
