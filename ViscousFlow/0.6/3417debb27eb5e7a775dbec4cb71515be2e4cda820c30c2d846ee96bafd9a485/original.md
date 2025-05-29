```
viscousflow_system(grid,[bodies];kwargs...)
```

Construct the operators and cache variables for a viscous flow problem.

The `kwargs` are the optional keyword aguments. There are several, some of which are crucial for certain types of problems.

  * `ddftype =` to set the DDF type. The default is `CartesianGrids.Yang3`.
  * `scaling =` to set the scaling type, `GridScaling` (default) or `IndexScaling`.
  * `dtype =` to set the element type to `Float64` (default) or `ComplexF64`.
  * `phys_params =` A dictionary to pass in physical parameters, or to pass in                 alternative models for the freestream velocity (with the "freestream" key)
  * `bc =` A dictionary to pass in boundary condition data or functions, using "external"         and "internal" keys to pass in functions that provide the         corresponding surface data outside and inside the surface(s).
  * `forcing =` A dictionary to pass in forcing models (via the "forcing models" key)
  * `motions =` to provide function(s) that specify the velocity of the immersed surface(s).
  * `reference_body =` to solve the problem in a reference frame attached to a body rather than             the inertial frame (with is the default, with body number 0).
  * `timestep_func =` to pass in a function for time-dependent problems that provides the time-step size.                 It is expected that this function takes in two arguments,                 the `grid::PhysicalGrid` and `phys_params`, and returns the time step.                 It defaults to the basic Fourier/CFL type function `default_timestep`
