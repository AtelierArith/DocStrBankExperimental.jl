```julia
struct SinCosRevolute{T} <: RigidBodyDynamics.JointType{T}
```

`SinCosRevolute` ジョイントタイプは、固定された軸の周りの回転を許可します。

[`Revolute`](@ref) ジョイントタイプとは対照的に、`SinCosRevolute` ジョイントタイプの構成ベクトルは、指定された軸の周りの回転角のサインとコサイン（その順序で）で構成されています。`SinCosRevolute` ジョイントタイプの速度ベクトルは、`Revolute` ジョイントタイプと同じであり、すなわち、軸の周りの角度の時間微分です。
