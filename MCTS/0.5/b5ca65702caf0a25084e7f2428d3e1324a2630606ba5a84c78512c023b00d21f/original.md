RolloutEstimator

If this is passed to the estimate_value field of the solver, rollouts will be used to estimate the value at the leaf nodes

Fields:     solver::Union{Solver,Policy,Function}         If this is a Solver, solve(solver, mdp) will be called to find the rollout policy         If this is a Policy, the policy will be used for rollouts         If this is a Function, a POMDPToolbox.FunctionPolicy with this function will be used for rollouts     max_depth::Int         Rollout depth. If this is -1, it will roll out to the `depth` argument of the `MCTSSolver` from the root node.     eps::Float64         A small number; if γᵗ where γ is the discount factor and t is the time step becomes smaller than this, the rollout will be terminated.
