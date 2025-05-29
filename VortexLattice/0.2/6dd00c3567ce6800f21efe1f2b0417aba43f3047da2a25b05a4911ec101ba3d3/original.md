```
trajectory_to_freestream(dt; kwargs...)
```

Convert trajectory parameters into freestream velocity parameters (see [`Freestream`](@ref)) at a collection of time steps.

# Arguments:

  * `dt`: Time step vector (seconds)

# Keyword Arguments:

  * `Xdot = zeros(length(dt))`: Global frame x-velocity for each time step
  * `Ydot = zeros(length(dt))`: Global frame y-velocity for each time step
  * `Zdot = zeros(length(dt))`: Global frame z-velocity for each time step
  * `p = zeros(length(dt))`: Angular velocity about x-axis for each time step
  * `q = zeros(length(dt))`: Angular velocity about y-axis for each time step
  * `r = zeros(length(dt))`: Angular velocity about z-axis for each time step
  * `phi0 = 0`: Roll angle for initial time step
  * `theta0 = 0`: Pitch angle for initial time step
  * `psi0 = 0`: Yaw angle for initial time step
