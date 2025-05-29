```
set_physics_state!(m::Model, d::Data, x::AbstractVector)
```

Set the state vector of a MuJoCo model.

The state vector is [joint positions, joint velocities, actuator states] with dimension (nq, nv, na). Call [`forward!`](@ref) after setting the state to compute all derived quantities in the `Data` object according to the new state.

See also [`mj_setState`](@ref) and [`get_physics_state`](@ref).
