```julia
struct WrenchesCache{M} <: RigidBodyDynamics.AbstractTypeDict
```

`BodyDict{Wrench{T}}`の作成と保存を管理するコンテナ。[`StateCache`](@ref)に似ています。
