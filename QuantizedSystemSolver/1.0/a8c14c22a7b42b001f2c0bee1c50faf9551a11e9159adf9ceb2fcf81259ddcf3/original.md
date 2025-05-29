```
solve(prob::NLODEProblem{F,PRTYPE,T,D,Z,CS},al::QSSAlgorithm{SolverType, OrderType},tspan::Tuple{Float64, Float64};detection::Val{M}=Val(3),saveat=Inf::Float64,abstol=1e-4::Float64,reltol=1e-3::Float64,maxErr=1.0::Float64,maxiters=Int(1e7)::Int) where{F,PRTYPE,T,D,Z,CS,SolverType,OrderType,M}
```

dispatches on a specific integrator based on the algorithm provided and send a nonlinear ODE problem to the integrator.

With the exception of the argument prob and tspan, all other arguments are optional and have default values:

  * The algorithm defaults to nmliqss2, and it is specified by the QSSAlgorithm type, which is a composite type that has a name and an order. It can be extended independently of the solver.
  * The detection argument defaults to 1.
  * The saveat argument defaults to Inf. It specifies the time step at which the integrator will save the solution (not implemented).
  * The abstol argument defaults to 1e-4. It specifies the absolute tolerance of the integrator.
  * The reltol argument defaults to 1e-3. It specifies the relative tolerance of the integrator.
  * The maxErr argument defaults to Inf. It specifies the maximum error allowed by the integrator. This is used as an upper bound for the quantum when a variable goes large.
  * The maxiters argument defaults to 1e7. It specifies the maximum number of steps allowed by the integrator. If the user wants to extend the limit on the maximum number of steps, this argument can be used.

After the simulation, the solution is returned as a Solution object.
