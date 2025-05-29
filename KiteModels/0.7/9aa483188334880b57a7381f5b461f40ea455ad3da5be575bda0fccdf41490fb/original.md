```
init_sim!(s::AKM; t_end=1.0, stiffness_factor=0.5, delta=0.001, upwind_dir=-pi/2, prn=false)
```

Initializes the integrator of the model.

Parameters:

  * s:     an instance of an abstract kite model
  * t_end: end time of the simulation; normally not needed
  * stiffness_factor: factor applied to the tether stiffness during initialization
  * delta: initial stretch of the tether during the steady state calculation
  * upwind_dir: upwind direction in radians, the direction the wind is coming from. Zero is at north;              clockwise positive. Default: -pi/2, wind from west.
  * prn: if set to true, print the detailed solver results

Returns: An instance of a DAE integrator.
