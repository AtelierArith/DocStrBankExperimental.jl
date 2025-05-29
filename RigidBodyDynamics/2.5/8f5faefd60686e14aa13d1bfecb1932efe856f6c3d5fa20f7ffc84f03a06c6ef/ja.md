```julia
struct Fixed{T} <: RigidBodyDynamics.JointType{T}
```

`Fixed` ジョイントタイプは、前の剛体と後の剛体の間に動きを許さないという意味で、退化したジョイントタイプです。
