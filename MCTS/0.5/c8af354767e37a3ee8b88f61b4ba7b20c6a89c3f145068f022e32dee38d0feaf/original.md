MCTS solver type

# Fields

  * `n_iterations::Int64=100` Number of iterations during each action() call.
  * `max_time::Float64=Inf` Maximum amount of CPU time spent iterating through simulations in seconds.
  * `depth::Int64=10`: Maximum tree search depth. Rollout depth is controlled via the `estimate_value` field.
  * `exploration_constant::Float64=1.0`: Specifies how much the solver should explore.  In the UCB equation, Q + c*sqrt(log(t/N)), c is the exploration constant.
  * `rng::AbstractRNG=Random.GLOBAL_RNG`: Random number generator
  * `estimate_value::Any=RolloutEstimator(RandomSolver(rng))`: Function, object, or number used to estimate the value at the leaf nodes (rollout policy).

      * If this is a function `f`, `f(mdp, s, remaining_depth)` will be called to estimate the value (remaining_depth can be ignored).
      * If this is an object `o`, `estimate_value(o, mdp, s, remaining_depth)` will be called.
      * If this is a number, the value will be set to that number
  * `init_Q::Any=0.0`: Function, object, or number used to set the initial Q(s,a) value at a new node.

      * If this is a function `f`, `f(mdp, s, a)` will be called to set the value.
      * If this is an object `o`, `init_Q(o, mdp, s, a)` will be called.
      * If this is a number, Q will be set to that number
  * `init_N::Any=0`: Function, object, or number used to set the initial N(s,a) value at a new node.

      * If this is a function `f`, `f(mdp, s, a)` will be called to set the value.
      * If this is an object `o`, `init_N(o, mdp, s, a)` will be called.
      * If this is a number, N will be set to that number
  * `reuse_tree::Bool=false`: If this is true, the tree information is re-used for calculating the next plan. Of course, clear_tree! can always be called to override this.
  * `enable_tree_vis::Bool=false`: If this is true, extra information needed for tree visualization will be recorded. If it is false, the tree cannot be visualized.
  * `timer::Function=()->1e-9*time_ns()`: Timekeeping method. Search iterations ended when `timer() - start_time ≥ max_time`.
