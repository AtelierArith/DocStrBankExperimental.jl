```
pdeval(m, xmesh, u_approx, x_eval, pb)
```

Function that interpolates with respect to the space component the solution obtained by the solver function [`pdepe`](@ref).

Input arguments:

  * `m`: symmetry of the problem (m=0,1,2 for cartesian, cylindrical or spherical).
  * `xmesh`: space discretization.
  * `u_approx`: approximate solution obtained by the solver `pdepe`.
  * `x_eval`: point or vector of points where to interpolate the approximate solution.
  * `pb`: structure defining the problem definition, see [`SkeelBerzins.ProblemDefinition`](@ref).

Returns a tuple $(u,dudx)$ corresponding to the solution and its partial derivative with respect to the space component evaluated in `x_eval`.
