```
multiple_shoot(p, ode_data, tsteps, ensembleprob, ensemblealg, loss_function,
    [continuity_loss = _default_continuity_loss], solver, group_size;
    continuity_term = 100, kwargs...)
```

Returns a total loss after trying a 'Direct multiple shooting' on ODE data and an array of predictions from each of the groups (smaller intervals). In Direct Multiple Shooting, the Neural Network divides the interval into smaller intervals and solves for them separately. The default continuity term is 100, implying any losses arising from the non-continuity of 2 different groups will be scaled by 100.

Arguments:

  * `p`: The parameters of the Neural Network to be trained.
  * `ode_data`: Original Data to be modelled.
  * `tsteps`: Timesteps on which ode_data was calculated.
  * `ensemble_prob`: Ensemble problem that the Neural Network attempts to solve.
  * `ensemble_alg`: Ensemble algorithm, e.g. `EnsembleThreads()`.
  * `prob`: ODE problem that the Neural Network attempts to solve.
  * `loss_function`: Any arbitrary function to calculate loss.
  * `continuity_loss`: Function that takes states $\hat{u}_{end}$ of group $k$ and $u_{0}$ of group $k+1$ as input and calculates prediction continuity loss between them. If no custom `continuity_loss` is specified, `sum(abs, û_end - u_0)` is used.
  * `solver`: ODE Solver algorithm.
  * `group_size`: The group size achieved after splitting the ode_data into equal sizes.
  * `continuity_term`: Weight term to ensure continuity of predictions throughout different groups.
  * `kwargs`: Additional arguments splatted to the ODE solver. Refer to the [Local Sensitivity Analysis](https://docs.sciml.ai/SciMLSensitivity/stable/) and [Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) documentation for more details.

!!! note
    The parameter 'continuity_term' should be a relatively big number to enforce a large penalty whenever the last point of any group doesn't coincide with the first point of next group.

