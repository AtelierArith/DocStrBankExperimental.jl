```
SweepX{ORDER}
```

A non-linear, time domain solver, that solves the problem time-step by time-step. Only the `X`-dofs of the model are solved for, while `U`-dofs and `A`-dofs are unchanged.

  * `SweepX{0}` is Newton-Raphson, with feasibility line-search, to handle inequality constraints.
  * `SweepX{1}` is implicit Euler, with feasibility line-search.
  * `SweepX{2}` is Newmark-β, with Newton-Raphson iterations and feasibility line search

IMPORTANT NOTE: Muscade does not allow elements to have state variables, for example, plastic strain, or shear-free position for dry friction.  Where the element implements such physics, this  is implemented by introducing the state as a degree of freedom of the element, and solving for its evolution, *even in a static problem*, requires the use of `ORDER≥1`

An analysis is carried out by a call with the following syntax:

```
initialstate    = initialize!(model)
setdof!(initialstate,1.;class=:U,field=:λcsr)
states           = solve(SweepX{2};initialstate=initialstate,time=0:10)
```

# Named arguments to `solve`:

  * `dbg=(;)`           a named tuple to trace the call tree (for debugging)
  * `verbose=true`      set to false to suppress printed output (for testing)
  * `silenterror=false` set to true to suppress print out of error (for testing)
  * `initialstate`      a `State`, obtain from `ìnitialize!` or `SweepX`.
  * `time`              maximum number of Newton-Raphson iterations
  * `β=1/4`,`γ=1/2`     parameters to the Newmark-β algorithm. Dummy if `ORDER<2`
  * `maxiter=50`        maximum number of equilibrium iterations at each step.
  * `maxΔx=1e-5`        convergence criteria: norm of `X`. D
  * `maxLλ=∞`           convergence criteria: norm of the residual.
  * `saveiter=false`    set to true so that output `states` contains the state                     at the iteration of the last step analysed.  Useful to study                     a step that fails to converge.
  * `maxLineIter=50`    Maximum number of iteration in the feasibility line search.                     set to 0 to skip the line search (not recommended for models                     with inequality constraints).
  * `sfac=0.5`          Parameter in the line search for a feasible point. If a                      tentative result is not feasible, backtrack by a factor `sfac`.                     If still not feasible, backtrack what is left by a factor `sfac`,                     and so forth, up to `maxLineIter` times.
  * `γfac=0.5`          Parameter for feasibility. For an inequality constraint `g(X)`                     with reaction force `λ`, require `g(X)*λ==γ`, and multiply                     `γ *= γfac` at each iteration.

# Output

A vector of length equal to that of the named input argument `time` containing the states at the time steps.                       

See also: [`solve`](@ref), [`initialize!`](@ref), [`findlastassigned`](@ref), [`studysingular`](@ref) 
