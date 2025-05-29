```
LagrangianParticles(; x, y, z, restitution=1.0, dynamics=no_dynamics, parameters=nothing)
```

モデルに渡すことができる `LagrangianParticles` を構築します。粒子は初期位置 `x`、`y`、および `z` を持ちます。粒子-壁衝突の反発係数は `restitution` によって指定されます。

`dynamics` は `(lagrangian_particles, model, Δt)` の関数で、粒子を移動させる前に呼び出されます。`parameters` は `dynamics` 関数内でアクセスできます。
