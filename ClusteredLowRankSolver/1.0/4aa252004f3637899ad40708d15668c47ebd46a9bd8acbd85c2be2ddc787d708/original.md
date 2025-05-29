```
	solvesdp(problem::Problem; kwargs...)
```

```
    solvesdp(sdp::ClusteredLowRankSDP; kwargs...)
```

Solve the semidefinite program generated from `problem` or `sdp`. 

Keyword arguments:

  * `prec` (default: `precision(BigFloat)`): the precision used
  * `gamma` (default: `0.9`): the step length reduction; a maximum step length of α reduces to a step length of `max(gamma*α,1)`
  * `beta_(in)feasible` (default: `0.1` (`0.3`)): the amount mu is tried to be reduced by in each iteration, for (in)feasible solutions
  * `omega_p/d` (default: `10^10`): the starting matrix variable for the primal/dual is `omega_p/d*I`
  * `maxiterations` (default: `500`): the maximum number of iterations
  * `duality_gap_threshold` (default: `10^-15`): how near to optimal the solution needs to be
  * `primal/dual_error_threshold` (default:`10^-30`): how feasible the primal/dual solution needs to be
  * `max_complementary_gap` (default: `10^100`): the maximum of `dot(X,Y)/nrows(X)` allowed
  * `need_primal_feasible/need_dual_feasible` (default: `false`): terminate when the solution is primal/dual feasible
  * `verbose` (default: `true`): print information after every iteration if true
  * `step_length_threshold` (default: `10^-7`): the minimum step length allowed
  * `primalsol` (default: `nothing`): start from the solution `(primalsol, dualsol)` if both `primalsol` and `dualsol` are given
  * `dualsol` (default: `nothing`): start from the solution `(primalsol, dualsol)` if both `primalsol` and `dualsol` are given
  * `safe_step` (default: `true`): use only 'safe' steps with step length at most 1, and take alpha*p = alpha*d when the the solution is primal and dual feasible
