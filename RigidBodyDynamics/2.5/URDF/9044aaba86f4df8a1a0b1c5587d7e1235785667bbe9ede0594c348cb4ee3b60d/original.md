```julia
parse_urdf(
    filename;
    scalar_type,
    floating,
    joint_types,
    root_joint_type,
    remove_fixed_tree_joints,
    gravity,
    revolute_joint_type,
    floating_joint_type
)

```

Create a `Mechanism` by parsing a [URDF](https://wiki.ros.org/urdf/XML/model) file.

Keyword arguments:

  * `scalar_type`: the scalar type used to store the `Mechanism`'s kinematic and inertial  properties. Default: `Float64`.
  * `floating`: whether to use a floating joint as the root joint. Default: false.
  * `joint_types`: dictionary mapping URDF joint type names to `JointType` subtypes.  Default: [`default_urdf_joint_types()`](@ref).
  * `root_joint_type`: the `JointType` instance used to connect the parsed `Mechanism` to the world.  Default: an instance of the the joint type corresponding to the `floating` URDF joint type tag  if `floating`, otherwise in an instance of the joint type for the `fixed` URDF joint type tag.
  * `remove_fixed_tree_joints`: whether to remove any fixed joints present in the kinematic tree  using [`remove_fixed_tree_joints!`](@ref). Default: `true`.
  * `gravity`: gravitational acceleration as a 3-vector expressed in the `Mechanism`'s root frame  Default: `[0.0, 0.0, -9.81]`.
