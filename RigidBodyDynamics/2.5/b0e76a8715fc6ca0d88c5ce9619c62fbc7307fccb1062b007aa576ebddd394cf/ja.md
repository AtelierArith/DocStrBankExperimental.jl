```julia
struct SegmentedVectorCache{K, KeyRange<:AbstractUnitRange{K}} <: RigidBodyDynamics.AbstractTypeDict
```

異種型の[`SegmentedVector`](@ref)オブジェクトの作成と保存を管理するコンテナ。[`StateCache`](@ref)に似ています。
