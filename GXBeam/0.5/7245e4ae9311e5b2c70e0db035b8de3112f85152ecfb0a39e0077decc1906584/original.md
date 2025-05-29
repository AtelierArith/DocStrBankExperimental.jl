```
set_state!([x,] system::StaticSystem, prescribed_conditions; kwargs...)
```

Set the state variables in `system` (or in the vector `x`) to the provided values.

# Keyword Arguments

  * `u`: Vector containing the linear displacement of each point.
  * `theta`: Vector containing the angular displacement of each point.
  * `F`: Vector containing the externally applied forces acting on each point
  * `M`: Vector containing the externally applied moments acting on each point
  * `Fi`: Vector containing internal forces for each beam element
  * `Mi`: Vector containing internal moments for each beam element
