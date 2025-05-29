```
set_state!([x,] system::ExpandedSystem, prescribed_conditions; kwargs...)
```

Set the state variables in `system` (or in the vector `x`) to the provided values.

# Keyword Arguments

  * `u`: Vector containing the linear displacement of each point.
  * `theta`: Vector containing the angular displacement of each point.
  * `V`: Vector containing the linear velocity of each point in the deformed point frame
  * `Omega` Vector containing the angular velocity of each point in the deformed point frame
  * `F`: Vector containing the externally applied forces acting on each point
  * `M`: Vector containing the externally applied moments acting on each point
  * `F1`: Vector containing resultant forces at the start of each beam element (in the  deformed element frame)
  * `M1`: Vector containing resultant moments at the start of each beam element (in the  deformed element frame)
  * `F2`: Vector containing resultant forces at the end of each beam element (in the  deformed element frame)
  * `M2`: Vector containing resultant moments at the end of each beam element (in the  deformed element frame)
  * `V_e`: Vector containing the linear velocity of each beam element in the deformed  beam element reference frame.
  * `Omega_e` Vector containing the angular velocity of each beam element in the deformed  beam element reference frame.
