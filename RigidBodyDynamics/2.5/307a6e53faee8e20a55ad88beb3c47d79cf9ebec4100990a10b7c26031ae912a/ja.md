```julia
struct Revolute{T} <: RigidBodyDynamics.JointType{T}
```

`Revolute` ジョイントタイプは、固定された軸の周りの回転を許可します。

`Revolute` ジョイントタイプの構成ベクトルは、指定された軸の周りの回転角度で構成されます。速度ベクトルは角速度であり、したがって構成ベクトルの時間微分です。
