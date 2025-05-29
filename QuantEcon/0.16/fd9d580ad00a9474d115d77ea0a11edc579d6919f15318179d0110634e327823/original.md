Solve the dynamic programming problem.

##### Parameters

  * `ddp::DiscreteDP` : Object that contains the Model Parameters
  * `method::Type{T<Algo}(VFI)`: Type name specifying solution method. Acceptable arguments are `VFI` for value function iteration or `PFI` for policy function iteration or `MPFI` for modified policy function iteration
  * `;max_iter::Int(250)` : Maximum number of iterations
  * `;epsilon::Float64(1e-3)` : Value for epsilon-optimality. Only used if `method` is `VFI`
  * `;k::Int(20)` : Number of iterations for partial policy evaluation in  modified policy iteration (irrelevant for other methods).

##### Returns

  * `ddpr::DPSolveResult{Algo}` : Optimization result represented as a `DPSolveResult`. See `DPSolveResult` for details.
