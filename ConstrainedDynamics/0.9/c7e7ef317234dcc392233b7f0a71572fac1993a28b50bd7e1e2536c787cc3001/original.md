```julia
mutable struct EqualityConstraint{T, N, Nc, Cs} <: ConstrainedDynamics.AbstractConstraint{T, N}
```

An `EqualityConstraint` is a component of a [`Mechanism`](@ref) and is used to describe the kinematic relation between two or more [`Body`](@ref)s.  Typically, an `EqualityConstraint` should not be created directly. Use the joint prototypes instead, for example: 

```julia
EqualityConstraint(Revolute(body1, body2, rotation_axis)).
```

# Important attributes

  * `id`:       The unique ID of a constraint. Assigned when added to a `Mechanism`.
  * `name`:     The name of a constraint. The name is taken from a URDF or can be assigned by the user.
  * `parentid`: The ID of the parent body.
  * `childids`: The IDs of the child bodies.
