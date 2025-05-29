```julia
geometric_jacobian(state, path)

```

Compute a geometric Jacobian (also known as a basic, or spatial Jacobian) associated with a directed path in the `Mechanism`'s spanning tree, (a collection of `Joint`s and traversal directions) in the given state.

A geometric Jacobian maps the `Mechanism`'s joint velocity vector $v$ to the twist of the target of the joint path (the body succeeding the last joint in the path) with respect to the source of the joint path (the body preceding the first joint in the path).

See also [`path`](@ref), [`GeometricJacobian`](@ref), [`Twist`](@ref).

The Jacobian is computed in the `Mechanism`'s root frame.

See [`geometric_jacobian!(out, state, path)`](@ref).
