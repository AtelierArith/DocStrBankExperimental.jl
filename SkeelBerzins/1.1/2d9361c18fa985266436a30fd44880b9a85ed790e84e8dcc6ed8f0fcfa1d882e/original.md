```
pdepe(m, pdefunction, icfunction, bdfunction, xmesh ; params=SkeelBerzins.Params(tstep=Inf), kwargs...)
```

Solve 1D elliptic PDE(s) using the spatial discretization method described in [1] - [`pdepe`](@ref) variant to solve stationary problems. Performs one step of the implicit Euler method.

Input arguments:

  * `m`: scalar referring to the symmetry of the problem. It can either take the value `m=0`, `m=1` or `m=2` representing cartesian, cylindrical or spherical coordinates respectively.
  * `pdefunction`: Function. Defines the formulation of the PDE(s) using capacity, flux and source terms (capacity term should be set to 0).
  * `icfunction`: Function. It defines the initial value(s) used for the Newton solver.
  * `bdfunction`: Function. Defines the boundary conditions of the problem.
  * `xmesh`: 1D array representing the spatial mesh on which the user intends to obtain the solution.

Keyword argument:

  * `params`: defines a [`SkeelBerzins.Params`](@ref) structure containing the keyword arguments from the solvers.
  * `kwargs`: instead of using the [`SkeelBerzins.Params`](@ref) struct, the user can pass directly fields from this particular struct to the solver.

Returns a 1D Array with the solution available at the points defined by the spatial discretization `xmesh`.
