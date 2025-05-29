```
get_physics_state(m::Model, d::Data)
```

Extract the state vector of a MuJoCo model.

The state vector is [joint positions, joint velocities, actuator states] with dimension (nq, nv, na). 

See also [`mj_getState`](@ref) and [`set_physics_state!`](@ref).
