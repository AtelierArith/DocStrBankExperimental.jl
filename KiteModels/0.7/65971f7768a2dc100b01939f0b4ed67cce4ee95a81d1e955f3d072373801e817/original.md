```
next_step!(s::AKM, integrator; set_speed = nothing, set_torque=nothing, set_force=nothing, bearing = nothing
           attractor=nothing, v_wind_gnd=s.set.v_wind, upwind_dir=-pi/2, dt=1/s.set.sample_freq)
```

Calculates the next simulation step. Either `set_speed` or `set_torque` must be provided.

Parameters:

  * s:            an instance of an abstract kite model
  * integrator:   an integrator instance as returned by the function [`init_sim!`](@ref)
  * set_speed:         set value of reel out speed in m/s or nothing
  * set_torque:   set value of the torque in Nm or nothing
  * set_force:    set value of the force in N or nothing (only for logging, not used otherwise)
  * bearing:      set value of heading/ course in radian or nothing (only for logging, not used otherwise)
  * attractor:    the attractor coordinates [azimuth, elevation] in radian or nothing (only for logging)
  * `v_wind_gnd`: wind speed at reference height in m/s
  * `upwind_dir`: upwind direction in radians, the direction the wind is coming from. Zero is at north;                clockwise positive. Default: -pi/2, wind from west.
  * dt:           time step in seconds

Returns: The end time of the time step in seconds.
