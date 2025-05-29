```julia
struct SPQuatFloating{T} <: RigidBodyDynamics.JointType{T}
```

A floating joint type that uses a modified Rodrigues parameter (`Rotations.MRP`, previously known as `Rotations.SPQuat`) representation for orientation.

Floating joints are 6-degree-of-freedom joints that are in a sense degenerate, as they impose no constraints on the relative motion between two bodies.

The 6-dimensional configuration vector of a `SPQuatFloating` joint type consists of a SPQuat representing the orientation that rotates vectors from the frame 'directly after' the joint to the frame 'directly before' it, and a 3D position vector representing the origin of the frame after the joint in the frame before the joint.

The 6-dimensional velocity vector of a `SPQuatFloating` joint is the twist of the frame after the joint with respect to the frame before it, expressed in the frame after the joint.
