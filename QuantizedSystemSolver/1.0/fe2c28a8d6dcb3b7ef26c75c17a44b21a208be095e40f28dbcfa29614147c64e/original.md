```
solve(prob::NLODEProblem{F,PRTYPE,T,D,Z,CS},al::QSSAlgorithm{SolverType, OrderType};detection::Val{M}=Val(3),saveat=Inf::Float64,abstol=1e-4::Float64,reltol=1e-3::Float64,maxErr=1.0::Float64,maxiters=Int(1e7)::Int,verbose=false::Bool) where{F,PRTYPE,T,D,Z,CS,SolverType,OrderType,M}
```

dispatches on a specific integrator based on the algorithm provided and send a nonlinear ODE problem to the integrator.

# Arguments

  * `prob::NLODEProblem{F,PRTYPE,T,D,Z,CS}`: The nonlinear ODE problem to solve.
  * `al::QSSAlgorithm{SolverType, OrderType}`: The QSS algorithm to use for solving the problem.
  * `detection::Val{M}`: A type parameter indicating which detection mechanism to use.
  * `saveat::Float64`: The time interval at which to save the solution (default: `Inf`).
  * `abstol::Float64`: The absolute tolerance for the solver (default: `1e-4`).
  * `reltol::Float64`: The relative tolerance for the solver (default: `1e-3`).
  * `maxErr::Float64`: The maximum allowable error (default: `Inf`).
  * `maxiters::Int`: The maximum number of iterations (default: `Int(1e7)`).
