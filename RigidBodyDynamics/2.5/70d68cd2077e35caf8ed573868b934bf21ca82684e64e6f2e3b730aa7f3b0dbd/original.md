```julia
submechanism(mechanism, submechanismroot; bodymap, jointmap)

```

Create a new `Mechanism` from the subtree of `mechanism` rooted at `submechanismroot`.

Any non-tree joint in `mechanism` will appear in the returned `Mechanism` if and only if both its successor and its predecessor are part of the subtree.

Keyword arguments:

  * `bodymap::AbstractDict{RigidBody{T}, RigidBody{T}}`: will be populated with the mapping from input mechanism's bodies to output mechanism's bodies
  * `jointmap::AbstractDict{<:Joint{T}, <:Joint{T}}`: will be populated with the mapping from input mechanism's joints to output mechanism's joints

where `T` is the element type of `mechanism`.
