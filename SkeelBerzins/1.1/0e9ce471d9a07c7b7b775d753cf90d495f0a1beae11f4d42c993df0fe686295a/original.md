```
pdepe(m, pdefunction, icfunction, bdfunction, xmesh, tspan ; params=SkeelBerzins.Params(), kwargs...)
```

Solve 1D elliptic and parabolic partial differential equation(s) using the spatial discretization method described in [1]. Note that to use this method, one of the PDEs must be parabolic. The time discretization is either done by the implicit Euler method (internal method) or by using a ODE/DAE solver from the [DifferentialEquations.jl](https://github.com/SciML/DifferentialEquations.jl) package. For more information on how to define the different inputs to solve a problem, look at the following sections: [Problem Definition](https://gregoirepourtier.github.io/SkeelBerzins.jl/dev/problem_definition/) and [Solvers](https://gregoirepourtier.github.io/SkeelBerzins.jl/dev/solvers/).

Input arguments:

  * `m`: scalar referring to the symmetry of the problem. It can either take the value `m=0`, `m=1` or `m=2` representing cartesian, cylindrical or spherical coordinates respectively.
  * `pdefunction`: Function. Defines the formulation of the PDE(s) using capacity, flux and source terms.
  * `icfunction`: Function. Defines the initial condition(s) of the problem to solve (if `tstep!=Inf` - initial condition(s) from the ODE/DAE problem, else if `tstep=Inf` - initial value(s) used for the newton solver).
  * `bdfunction`: Function. Defines the boundary conditions of the problem.
  * `xmesh`: 1D array representing the spatial mesh on which the user intends to obtain the solution.
  * `tspan`: tuple $(t_0, t_{end})$ representing the time interval of the problem.

Keyword argument:

  * `params`: defines a [`SkeelBerzins.Params`](@ref) struct containing the keyword arguments from the solvers.
  * `kwargs`: instead of using the [`SkeelBerzins.Params`](@ref) struct, the user can pass directly fields from this particular struct to the solver.

Returns a [`RecursiveArrayTools.DiffEqArray`](https://docs.sciml.ai/RecursiveArrayTools/stable/array_types/#RecursiveArrayTools.DiffEqArray) or a [`SkeelBerzins.ProblemDefinition`](@ref) struct, depending on the selected solver (either :euler or :DiffEq). The obtained solution includes a linear interpolation method in time and can be used to evaluate the solution at any time step within the interval $(t_0,t_{end})$ (accessible using `sol(t)`). A spatial interpolation similar as the [`pdeval`](@ref) function is available on the solution object using the command `sol(x_eval,t,pb)`.
