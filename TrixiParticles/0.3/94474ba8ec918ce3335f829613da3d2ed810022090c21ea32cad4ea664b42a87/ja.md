```
BoundaryModelMonaghanKajtar(K, beta, boundary_particle_spacing, mass;
                            viscosity=nothing)
```

`BoundarySPHSystem`の境界モデル。

# 引数

  * `K`: 反発力のスケーリングファクター。
  * `beta`: 流体粒子間隔と境界粒子間隔の比率。
  * `boundary_particle_spacing`: 境界粒子間隔。
  * `mass`: 各境界粒子の質量を保持するベクター。

# キーワード

  * `viscosity`: 自由滑り（デフォルト）またはノースリップ条件。詳細については上記の説明を参照してください。
