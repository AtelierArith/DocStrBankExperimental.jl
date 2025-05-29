```julia
struct DynamicsResultCache{M} <: RigidBodyDynamics.AbstractTypeDict
```

さまざまなスカラー型の[`DynamicsResult`](@ref)オブジェクトの作成と保存を管理するコンテナで、特定の`Mechanism`に関連付けられています。[`StateCache`](@ref)に似ています。
