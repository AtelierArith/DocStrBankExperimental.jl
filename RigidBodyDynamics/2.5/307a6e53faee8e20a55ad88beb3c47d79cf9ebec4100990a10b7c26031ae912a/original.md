```julia
struct Revolute{T} <: RigidBodyDynamics.JointType{T}
```

A `Revolute` joint type allows rotation about a fixed axis.

The configuration vector for the `Revolute` joint type simply consists of the angle of rotation about the specified axis. The velocity vector consists of the angular rate, and is thus the time derivative of the configuration vector.
