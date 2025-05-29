```julia
struct Joint{T, JT<:RigidBodyDynamics.JointType{T}}
```

A joint represents a kinematic restriction of the relative twist between two rigid bodies to a linear subspace of dimension $k$.

A joint has a direction. The rigid body before the joint is called the joint's predecessor, and the rigid body after the joint is its successor.

The state related to the joint is parameterized by two sets of variables, namely

  * a vector $q \in \mathcal{Q}$, parameterizing the relative homogeneous transform.
  * a vector $v \in \mathbb{R}^k$, parameterizing the relative twist.

The twist of the successor with respect to the predecessor is a linear function of $v$.

For some joint types (notably those using a redundant representation of relative orientation, such as a unit quaternion), $\dot{q}$, the time derivative of $q$, may not be the same as $v$. However, an invertible linear transformation exists between $\dot{q}$ and $v$.

See also:

  * Definition 2.9 in Duindam, "Port-Based Modeling and Control for Efficient Bipedal Walking Robots", 2006.
  * Section 4.4 of Featherstone, "Rigid Body Dynamics Algorithms", 2008.
