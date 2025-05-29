```julia
struct Fixed{T} <: RigidBodyDynamics.JointType{T}
```

The `Fixed` joint type is a degenerate joint type, in the sense that it allows no motion between its predecessor and successor rigid bodies.
