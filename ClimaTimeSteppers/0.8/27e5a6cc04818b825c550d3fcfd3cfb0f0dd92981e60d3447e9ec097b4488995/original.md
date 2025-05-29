```
ClimaTimeSteppers
```

Ordinary differential equation solvers

JuliaDiffEq terminology:

  * *Function*: the right-hand side function df/dt.

      * by default, a function gets wrapped in an `ODEFunction`
      * define new `IncrementingODEFunction` to support incrementing function calls.
  * *Problem*: Function, initial u, time span, parameters and options

    `du/dt = f(u,p,t) = fL(u,p,t)  + fR(u,p,t)`

    `fR(u,p,t) == f(u.p,t) - fL(u,p,t)` `fL(u,_,_) == A*u for some`A`(matrix free)`

    SplitODEProlem(fL, fR)

  * `ODEProblem` from SciMLBase.jl

      * use `jac` option to `ODEFunction` for linear + full IMEX (https://docs.sciml.ai/latest/features/performance*overloads/#ode*explicit_jac-1)
  * `SplitODEProblem` for linear + remainder IMEX
  * `MultirateODEProblem` for true multirate
  * *Algorithm*: small objects (often singleton) which indicate what algorithm + options (e.g. linear solver type)
  * define new abstract `DistributedODEAlgorithm`, algorithms in this pacakge will be subtypes of this
  * define new `Multirate` for multirate solvers
  * *Integrator*: contains everything necessary to solve. Used as:
  * define new `DistributedODEIntegrator` for solvers in this package

    init(prob, alg, options...) => integrator   step!(int) => runs single step   solve!(int) => runs it to end   solve(prob, alg, options...) => init + solve!
  * *Solution* (not implemented): contains the "solution" to the ODE.
