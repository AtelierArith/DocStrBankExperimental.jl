```
RealTimeDynamicPlanner(;
    heuristic::Heuristic = GoalCountHeuristic(),
    n_rollouts::Int = 50,
    max_depth::Int = 50,
    rollout_noise::Float64 = 0.0,
    action_noise::Float64 = 0.0,
    verbose::Bool = false,
    callback = verbose ? LoggerCallback() : nothing
)
```

Planner that uses Real Time Dynamic Programming (`RTDP` for short), a form of asynchronous value iteration which performs greedy rollouts from the initial state, updating the value estimates of states encountered along the way [1].

If a `heuristic` is provided, the negated heuristic value will be used as an initial value estimate for newly encountered states (since the value of a state in a shortest path problem is the cost to reach the goal), thereby guiding early rollouts.

For admissible (i.e. optimistic) heuristics, convergence to the true value function is guaranteed in the reachable state space after a sufficient number of rollouts.

Returns a [`TabularPolicy`](@ref) (wrapped in a [`BoltzmannPolicy`](@ref) if `action_noise > 0`), which stores the value estimates and action Q-values for each encountered state. 

[1] A. G. Barto, S. J. Bradtke, and S. P. Singh, "Learning to Act using Real-Time Dynamic Programming," Artificial Intelligence, vol. 72, no. 1, pp. 81–138, Jan. 1995, [https://doi.org/10.1016/0004-3702(94)00011-O](https://doi.org/10.1016/0004-3702(94)00011-O).

# Arguments

  * `heuristic`: Search heuristic used to initialize the value function.
  * `n_rollouts`: Number of rollouts to perform from the initial state.
  * `max_depth`: Maximum depth of each rollout.
  * `rollout_noise`: Amount of Boltzmann noise during simulated rollouts.
  * `action_noise`: Amount of Boltzmann action noise for the returned policy.
  * `verbose`: Flag to print debug information during search.
  * `callback`: Callback function for logging, etc.
