```julia
configuration_derivative_to_velocity!(v, joint, q, q̇)

```

Compute joint velocity vector $v$ given the joint configuration vector $q$ and its time derivative $\dot{q}$ (in place).

Note that this mapping is linear.

See also [`velocity_to_configuration_derivative!`](@ref), the inverse mapping.
