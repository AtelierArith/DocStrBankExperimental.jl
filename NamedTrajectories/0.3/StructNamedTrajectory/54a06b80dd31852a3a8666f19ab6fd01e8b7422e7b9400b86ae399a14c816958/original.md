```
NamedTrajectory(component_data; controls=(), timestep=nothing, bounds, initial, final, goal)

# Arguments
- `component_data::NamedTuple{names, <:Tuple{Vararg{AbstractMatrix{R}}}} where {names}`: Components data.
- `controls`: The control variable in component_data, should be type of `Symbol` among `component_data`.
- `timestep`: Discretizing time step in `component_data`, should be type of `Symbol` among `component_data`.
- `bounds`: Bounds of the trajectory.
- `initial`: Initial values.
- `final`: Final values.
- `goal`: Goal for the states.
```
