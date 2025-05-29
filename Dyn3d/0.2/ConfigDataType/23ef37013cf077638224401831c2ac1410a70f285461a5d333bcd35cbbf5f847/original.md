```
ConfigJoint(njoint,joint_type,shape1,shape2,body1,joint_dof,qJ_init)
```

Set up configuration information for a single joint. A joint allows one/multiple degree of freedoms from 1 to 6.

## Fields

  * `njoint`: Int, total number of joints for this body-joint system
  * `joint_type`: String, allows "revolute", "prismatic", "cylindrical", "planar",   "spherical", "free" and "custom". Detailed information is described in `JointType`   section
  * `shape1`: Vector{Float64} with 6 elements. It describes the location of this   joint in its parent body coordinate. If shape1 is used on the first joint,   then it's the orientation of this first joint to inertial system. It is written   with [θx, θy, θz, x, y, z].
  * `shape2`: Vector{Float64} with 6 elements. It describes the location of this   joint in its child body coordinate. Normally, shape2 is zeros(Float64,6) if   there's no distance gap or angle gap between two adjacent bodies.
  * `body1`: the parent body id of this joint
  * `joint_dof`: Vector{Float64}. The size of joint_dof depends on the number of   specified dof, refers to type `Dof`.
  * `qJ_init`: Vector{Float64}. It is the initial angle/displacement of this joint   with respect to its parent body. The size should be the same as the number of   dof specified.
  * `vJ_init`: Vector{Float64}. It is the initial angular velocity of this joint   in its local frame. The size should be the same as the number of   dof specified.
