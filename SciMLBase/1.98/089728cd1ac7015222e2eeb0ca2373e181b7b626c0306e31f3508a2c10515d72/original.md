```julia
struct RODESolution{T, N, uType, uType2, DType, tType, randType, P, A, IType, S, AC<:Union{Nothing, Vector{Int64}}} <: SciMLBase.AbstractRODESolution{T, N, uType}
```

Representation of the solution to an stochastic differential equation defined by an SDEProblem, or of a random ordinary differential equation defined by an RODEProblem.

## DESolution Interface

For more information on interacting with `DESolution` types, check out the Solution Handling page of the DifferentialEquations.jl documentation.

https://docs.sciml.ai/DiffEqDocs/stable/basics/solution/

## Fields

  * `u`: the representation of the SDE or RODE solution. Given as an array of solutions, where `u[i]` corresponds to the solution at time `t[i]`. It is recommended in most cases one does not access `sol.u` directly and instead use the array interface described in the Solution Handling page of the DifferentialEquations.jl documentation.
  * `t`: the time points corresponding to the saved values of the ODE solution.
  * `W`: the representation of the saved noise process from the solution. See [the Noise Processes page of the DifferentialEquations.jl](https://docs.sciml.ai/DiffEqDocs/stable/features/noise_process/). Note that this noise is only saved in full if `save_noise=true` in the solver.
  * `prob`: the original SDEProblem/RODEProblem that was solved.
  * `alg`: the algorithm type used by the solver.
  * `stats`: statistics of the solver, such as the number of function evaluations required, number of Jacobians computed, and more.
  * `retcode`: the return code from the solver. Used to determine whether the solver solved successfully, whether it terminated early due to a user-defined callback, or whether it exited due to an error. For more details, see [the return code documentation](https://docs.sciml.ai/SciMLBase/stable/interfaces/Solutions/#retcodes).
