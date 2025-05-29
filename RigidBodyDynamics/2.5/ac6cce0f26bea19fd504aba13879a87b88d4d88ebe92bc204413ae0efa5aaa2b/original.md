```julia
struct SinCosRevolute{T} <: RigidBodyDynamics.JointType{T}
```

A `SinCosRevolute` joint type allows rotation about a fixed axis.

In contrast to the [`Revolute`](@ref) joint type, the configuration vector for the `SinCosRevolute` joint type consists of the sine and cosine of the angle of rotation about the specified axis (in that order). The velocity vector for the `SinCosRevolute` joint type is the same as for the `Revolute` joint type, i.e., the time derivative of the angle about the axis.
