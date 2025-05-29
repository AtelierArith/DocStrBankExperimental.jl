```
PrescribedConditions(; kwargs...)
```

Define the prescribed conditions at a point.  Individual prescribed conditions may be assigned as either a scalar parameter or as a function of time.

Prescribed Wiener-Milenkovic parameters must satisfy the following inequality: sqrt(theta*x^2 + theta*y^2 + theta_z^2) <= 4.  Note that this restriction still allows all possible rotations to be represented.

Note that if displacements and loads corresponding to the same degree of freedom are prescribed at the same point, the global body-fixed acceleration corresponding to the same degree of freedom will be modified to attempt to satisfy both conditions.

# Keyword Arguments

  * `ux`: Prescribed x-displacement (in the body frame)
  * `uy`: Prescribed y-displacement (in the body frame)
  * `uz`: Prescribed z-displacement (in the body frame)
  * `theta_x`: Prescribed first Wiener-Milenkovic parameter
  * `theta_y`: Prescribed second Wiener-Milenkovic parameter
  * `theta_z`: Prescribed third Wiener-Milenkovic parameter
  * `Fx`: Prescribed x-direction force
  * `Fy`: Prescribed y-direction force
  * `Fz`: Prescribed z-direction force
  * `Mx`: Prescribed x-direction moment
  * `My`: Prescribed y-direction moment
  * `Mz`: Prescribed z-direction moment
  * `Fx_follower`: Prescribed x-direction follower force
  * `Fy_follower`: Prescribed y-direction follower force
  * `Fz_follower`: Prescribed z-direction follower force
  * `Mx_follower`: Prescribed x-direction follower moment
  * `My_follower`: Prescribed y-direction follower moment
  * `Mz_follower`: Prescribed z-direction follower moment
