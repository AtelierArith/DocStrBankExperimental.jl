```
LagrangianParticles(particles::StructArray; restitution=1.0, tracked_fields::NamedTuple=NamedTuple(), dynamics=no_dynamics)
```

モデルに渡すことができる `LagrangianParticles` を構築します。`particles` は `StructArray` であり、カスタムフィールドを含むことができます。粒子-壁衝突の反発係数は `restitution` によって指定されます。

いくつかの `tracked_fields` をフィールドの `NamedTuple` として渡すことができます。各粒子は各フィールドの値を追跡します。各追跡フィールドには対応する粒子プロパティが必要です。したがって、`T` が追跡フィールドである場合、`T` もカスタム粒子プロパティでなければなりません。

`dynamics` は `(lagrangian_particles, model, Δt)` の関数であり、粒子を移動させる前に呼び出されます。`parameters` は `dynamics` 関数内でアクセスできます。
