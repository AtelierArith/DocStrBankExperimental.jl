```julia
parambounds(mode::MomentMatching.EstimationMode)

```

Returns five vectors:

  * `full_labels` contains the list of names of parameters which are possibly estimated under the current mode.
  * `full_lb_hard` contains a hard lower bound for each parameters. If any of these bounds are violated in local stage, model moments are not computed, but instead a penalty term is returned as objective function value. For formula see [`solve_inner`](@ref). Setting values to -Inf corresponds to no lower bound.
  * `full_lb_global` and
  * `full_ub_global` are lower and upper bounds for setting up the Sobol sequence. These vectors define the parameter subspace investigated in the global part of estimation.
  * `full_ub_hard` contains a hard upper bound for each parameters. Same as full*lb*hard applies. Setting values to Inf corresponds to no upper bound.

Should be defined for any subtype of [`EstimationMode`](@ref).
