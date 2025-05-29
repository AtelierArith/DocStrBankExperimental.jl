```
solve(system; kwargs...)
```

Built-in solution method for [`VoronoiFVM.System`](@ref).  

Keyword arguments:

  * General for all solvers 

      * `inival` (default: 0) : Array created via [`unknowns`](@ref) or  number giving the initial value.
      * `control` (default: nothing): Pass instance of [`SolverControl`](@ref)
      * All elements of [`SolverControl`](@ref) can be used as kwargs. Eventually overwrites values given via `control`
      * `params`: Parameters (Parameter handling is experimental and may change)
  * **Stationary solver**: Invoked if neither `times` nor `embed`, nor `tstep` are given as keyword argument.

      * `time` (default: `0.0`): Set time value.

    Returns a [`DenseSolutionArray`](@ref) or [`SparseSolutionArray`](@ref)
  * **Embedding (homotopy) solver**: Invoked if `embed` kwarg is given. Use homotopy embedding + damped Newton's method  to  solve stationary problem or to solve series of parameter dependent problems. Parameter step control is performed according to solver control data.  kwargs and default values are:

      * `embed` (default: `nothing` ): vector of parameter values to be reached exactly

    In addition,  all kwargs of the implicit Euler solver (besides `times`) are handled.   Returns a transient solution object `sol` containing the stored solution(s),  see [`TransientSolution`](@ref).
  * **Implicit Euler transient solver**: Invoked if `times` kwarg is given. Use implicit Euler method  + damped   Newton's method  to  solve time dependent problem. Time step control is performed according to solver control data.  kwargs and default values are:

      * `times` (default: `nothing` ): vector of time values to be reached exactly
      * `pre` (default: `(sol,t)->nothing` ):  callback invoked before each time step
      * `post`  (default:  `(sol,oldsol, t, Δt)->nothing` ): callback invoked after each time step
      * `sample` (default:  `(sol,t)->nothing` ): callback invoked after timestep for all times in `times[2:end]`.
      * `delta` (default:  `(system, u,v,t, Δt)->norm(sys,u-v,Inf)` ):  Value  used to control the time step size `Δu`

    If `control.handle_error` is true, if time step solution  throws an error, stepsize  is lowered, and  step solution is called again with a smaller time value. If `control.Δt<control.Δt_min`, solution is aborted with error. Returns a transient solution object `sol` containing the stored solution,  see [`TransientSolution`](@ref).
  * **Implicit Euler timestep solver**.  Invoked if `tstep` kwarg is given. Solve one time step of the implicit Euler method.

      * `time` (default: `0`): Set time value.
      * `tstep`: time step

    Returns a [`DenseSolutionArray`](@ref) or [`SparseSolutionArray`](@ref)
