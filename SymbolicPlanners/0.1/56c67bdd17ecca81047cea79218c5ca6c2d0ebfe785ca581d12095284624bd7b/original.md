```
MonteCarloTreeSearch(
	n_rollouts::Int64 = 50,
	max_depth::Int64 = 50,
	heuristic::Heuristic = NullHeuristic(),
	selector::MCTSNodeSelector = BoltzmannUCBSelector(),
	estimator::MCTSLeafEstimator = RandomRolloutEstimator()
end
```

Planner that uses Monte Carlo Tree Search (`MCTS` for short) [1], with a  customizable initial value `heuristic`, node `selector` strategy, and leaf node value `estimator`.

# Arguments

  * `n_rollouts`: Number of search rollouts to perform.
  * `max_depth`: Maximum depth of rollout (including the selection and estimation phases).
  * `heuristic`: Initial value heuristic for newly encountered states / leaf nodes.
  * `selector`: Node selection strategy for previously visited nodes (e.g. MaxUCB).
  * `estimator`: Estimator for leaf node values (e.g. random or policy-based rollouts).
