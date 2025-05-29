```julia
struct Planar{T} <: RigidBodyDynamics.JointType{T}
```

The `Planar` joint type allows translation along two orthogonal vectors, referred to as $x$ and $y$, as well as rotation about an axis $z = x \times y$.

The components of the 3-dimensional configuration vector $q$ associated with a `Planar` joint are the $x$- and $y$-coordinates of the translation, and the angle of rotation $\theta$ about $z$, in that order.

The components of the 3-dimension velocity vector $v$ associated with a `Planar` joint are the $x$- and $y$-coordinates of the linear part of the joint twist, expressed in the frame after the joint, followed by the $z$-component of the angular part of this joint twist.

!!! warning
    For the `Planar` joint type, $v \neq \dot{q}$! Although the angular parts of $v$ and $\dot{q}$ are the same, their linear parts differ. The linear part of $v$ is the linear part of $\dot{q}$, rotated to the frame after the joint. This parameterization was chosen to allow the translational component of the joint transform to be independent of the rotation angle $\theta$ (i.e., the rotation is applied **after** the translation), while still retaining a constant motion subspace expressed in the frame after the joint.

