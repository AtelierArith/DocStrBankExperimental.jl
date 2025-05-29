```julia
attach!(
    mechanism,
    parentbody,
    childmechanism;
    child_root_pose,
    bodymap,
    jointmap
)

```

Attach a copy of `childmechanism` to `mechanism`.

Essentially replaces the root body of a copy of `childmechanism` with `parentbody` (which belongs to `mechanism`).

Note: gravitational acceleration for `childmechanism` is ignored.

Keyword arguments:

  * `child_root_pose`: pose of the default frame of the root body of `childmechanism` relative to that of `parentbody`. Default: the identity transformation.
  * `bodymap::AbstractDict{RigidBody{T}, RigidBody{T}}`: will be populated with the mapping from input mechanism's bodies to output mechanism's bodies
  * `jointmap::AbstractDict{<:Joint{T}, <:Joint{T}}`: will be populated with the mapping from input mechanism's joints to output mechanism's joints

where `T` is the element type of `mechanism`.
