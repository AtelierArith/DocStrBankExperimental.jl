```julia
maximal_coordinates(
    mechanism;
    floating_joint_type,
    bodymap,
    jointmap
)

```

Return a dynamically equivalent `Mechanism`, but with a flat tree structure: all bodies are attached to the root body via a floating joint, and the tree joints of the input `Mechanism` are transformed into non-tree joints (with joint constraints enforced using Lagrange multipliers in `dynamics!`).

Keyword arguments:

  * `floating_joint_type::Type{<:JointType{T}}`: which floating joint type to use for the joints between each body and the root. Default: `QuaternionFloating{T}`
  * `bodymap::AbstractDict{RigidBody{T}, RigidBody{T}}`: will be populated with the mapping from input mechanism's bodies to output mechanism's bodies
  * `jointmap::AbstractDict{<:Joint{T}, <:Joint{T}}`: will be populated with the mapping from input mechanism's joints to output mechanism's joints

where `T` is the element type of `mechanism`.
