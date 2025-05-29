```
BendersAlgorithm(graph, root_object; kwargs...)
```

Function for creating the BendersAlgorithm object from `graph`. `root_object` must be an OptiNode or subgraph on `graph`. key ward arguments include the following

  * `max_iters = 100` - maximum number of iterations
  * `tol = 1e-7` - termination tolerance between upper and lower bounds
  * `M = 0` - lower bound on cost-to-go estimator for each node
  * `is_MIP = nothing` - indicates if the problem is a MIP. If it is passed as `nothing`,  PlasmoBenders will check to see if it is a MIP, and will set `is_MIP` accordingly
  * `solver = nothing` - if defined, this solver will be set for all subproblems
  * `strengthened = false` - whether to use strengthened Benders cuts (see https://doi.org/10.1007/s10107-018-1249-5.)
  * `multicut = true` - whether to use multicuts (rather than aggregated cuts) when applicable
  * `feasibility_cuts = false` - whether to allow feasibility cuts
  * `regularize = false` - whether to regularize solution of next iterates
  * `parallelize_benders = false` - whether to parallelize subproblem solution when the problem has a Benders-type structure defined
  * `parallelize_forward = false` - whether to parallelize forward pass if possible; not yet supported
  * `parallelize_backward = false` - whether to parallelize backward pass
  * `add_slacks::Bool = false` - whether to add slack variables to the linking constraints to  help ensure feasibility between solutions; slack variables are penalized in objective
  * `fix_slacks = false` - whether to fix the slack variables to zero they only relax if a problem is infeasible
  * `warm_start::Bool = true` - whether to set the previous iterations solutions as the  starting values for the next iterations forward pass
  * `relaxed_init_cuts = false` - whether to generate initial cuts by relaxing the problem and solving the whole problem; only applies for MILPs
  * `slack_penalty = 1e6` - coefficient on slack variables in objective
  * `regularize_param = 0.5` - regularization parameter; must be between 0 and 1
