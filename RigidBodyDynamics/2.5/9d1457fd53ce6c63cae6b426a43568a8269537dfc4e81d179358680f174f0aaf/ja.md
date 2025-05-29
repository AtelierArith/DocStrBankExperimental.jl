```julia
struct Prismatic{T} <: RigidBodyDynamics.JointType{T}
```

`Prismatic` ジョイントタイプは、固定された軸に沿った移動を許可します。
