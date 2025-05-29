```
PDMPProblem(F, R, Delta, nu, xc0, xd0, p, tspan)
```

Create a PDMP problem to be simulated. To define a PDMP Problem, you first need to give the function `F` and the initial condition `xc0` which define an ODE: dxc/dt = F(xc(t),xd(t),p,t). Jumps are defined as a Jump process which changes states at some rate `R`. Note, that in between jumps, `xd` is constant but `xc` is allowed to evolve.

## Arguments

  * `F`: inplace function `F(du, u, p, t)` representing the vector field
  * `R`: the function to compute the transition rates. It should be specified in-place as `R(rate::AbstractVector, xc, xd, p, t, issum::Bool)` where it mutates `rate`. Note that a boolean `issum` is provided and the behavior of `R` should be as follows

    1. if `issum == true`, we only require `R` to return the total rate, *e.g.* `sum(rate)`. We use this formalism because sometimes you can compute the `sum` without mutating `rate`.
    2. if `issum == false`, `R` must populate `rate` with the updated rates

We then need to provide the way the jumps affect the state variable. There are two possible ways here:     1. either give a transition matrix `nu`: it will only affect the discrete component `xd` and leave `xc` unaffected.     2. give a function to implement jumps `Delta(xc, xd, parms, t, ind_reaction::Int64)` where you can mutate `xc,xd` or `parms`. The argument `ind_reaction` is the index of the reaction at which the jump occurs. See `examples/pdmp_example_eva.jl` for an example.

  * `Delta` [Optional]: the function to effect the jumps
  * `nu` [Optional]: the transition matrix
  * `xc0`: the initial condition of the continuous part
  * `xd0`: the initial condition of the discrete part
  * `p`: the parameters to be provided to the functions `F, R, Delta`
  * `tspan`: The timespan for the problem.

## Constructors

  * `PDMPProblem(F,R,Delta,nu,xc0,xd0,p,tspan)`
  * `PDMPProblem(F,R,nu,xc0,xd0,p,tspan)` when ones does not want to provide the function `Delta`
  * `PDMPProblem(F,R,Delta,reaction_number::Int64,xc0,xd0,p,tspan)` when ones does not want to provide the transition matrix `nu`. The length `reaction_number` of the rate vector must then be provided.

We also provide a wrapper to [JumpProcesses.jl](https://github.com/SciML/JumpProcesses.jl). This is quite similar to how a `JumpProblem` would be created.

  * `PDMPProblem(prob, jumps...)` where `prob` can be an `ODEProblem`. For an example, please consider `example/examplediffeqjumpwrapper.jl`.
