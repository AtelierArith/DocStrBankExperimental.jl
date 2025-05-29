```julia
local_coordinates!(ϕ, ϕ̇, joint, q0, q, v)

```

Compute a vector of local coordinates $\phi$ around configuration $q_0$ corresponding to configuration $q$ (in place). Also compute the time derivative $\dot{\phi}$ of $\phi$ given the joint velocity vector $v$.

The local coordinate vector $\phi$ must be zero if and only if $q = q_0$.

For revolute or prismatic joint types, the local coordinates can just be $\phi = q - q_0$, but for joint types with configuration vectors that are restricted to a manifold (e.g. when unit quaternions are used to represent orientation), elementwise subtraction may not make sense. For such joints, exponential coordinates could be used as the local coordinate vector $\phi$.

See also [`global_coordinates!`](@ref).
