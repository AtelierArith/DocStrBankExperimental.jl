```julia
velocity_to_configuration_derivative!(q̇, joint, q, v)

```

Compute the time derivative $\dot{q}$ of the joint configuration vector $q$ given $q$ and the joint velocity vector $v$ (in place).

Note that this mapping is linear.

See also [`configuration_derivative_to_velocity!`](@ref), the inverse mapping.
