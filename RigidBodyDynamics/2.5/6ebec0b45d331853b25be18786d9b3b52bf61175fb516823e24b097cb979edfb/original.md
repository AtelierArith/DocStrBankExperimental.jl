```julia
struct QuaternionSpherical{T} <: RigidBodyDynamics.JointType{T}
```

The `QuaternionSpherical` joint type allows rotation in any direction. It is an implementation of a ball-and-socket joint.

The 4-dimensional configuration vector $q$ associated with a `QuaternionSpherical` joint is the unit quaternion that describes the orientation of the frame after the joint with respect to the frame before the joint. In other words, it is the quaternion that can be used to rotate vectors from the frame after the joint to the frame before the joint.

The 3-dimensional velocity vector $v$ associated with a `QuaternionSpherical` joint is the angular velocity of the frame after the joint with respect to the frame before the joint, expressed in the frame after the joint (body frame).
