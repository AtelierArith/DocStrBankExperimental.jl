The Metropolis-Adjusted Langevin Algorithm with automatic step size selection.

Briefly, at each iteration, the step size is exponentially shrunk or grown until the acceptance rate is in a reasonable range. A reversibility check ensures that the move is reversible with respect to the target. The process is started at `step_size`, which at the end of each round is set to the average exponent used across all chains.

The number of steps per exploration is set to `base_n_refresh * ceil(Int, dim^exponent_n_refresh)`.

At each round, an empirical diagonal marginal standard deviation matrix is estimated. At each step, a random interpolation between the identity and the estimated standard deviation is used to condition the problem.

In normal circumstance, there should not be a need for tuning, however the following optional keyword parameters are available:

  * `base_n_refresh`: The base number of steps (equivalently, momentum refreshments) between swaps. This base number gets multiplied by `ceil(Int, dim^(exponent_n_refresh))`.

  * `exponent_n_refresh`: Used to scale the increase in number of refreshment with dimensionality.

  * `default_autodiff_backend`: The default backend to use for autodiff. See https://github.com/tpapp/LogDensityProblemsAD.jl#backends

    Certain targets may ignore it, e.g. if a manual differential is offered or when calling an external program such as Stan.

  * `step_size`: Starting point for the automatic step size algorithm. Gets updated automatically between each round.

  * `preconditioner`: A strategy for building a preconditioner.

  * `estimated_target_std_deviations`: This gets updated after first iteration; initially `nothing` in which case an identity mass matrix is used.

Reference: Biron-Lattes, M., Surjanovic, N., Syed, S., Campbell, T., & Bouchard-Côté, A.. (2024).  [autoMALA: Locally adaptive Metropolis-adjusted Langevin algorithm](https://proceedings.mlr.press/v238/biron-lattes24a.html).  *Proceedings of The 27th International Conference on Artificial Intelligence and Statistics*,  in *Proceedings of Machine Learning Research* 238:4600-4608.
