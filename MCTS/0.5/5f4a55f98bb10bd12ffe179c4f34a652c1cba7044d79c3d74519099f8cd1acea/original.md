MCTS solver with DPW

# Fields

  * `depth::Int64=10`: Maximum tree search depth. Rollout depth is controlled via the `estimate_value` field.
  * `exploration_constant::Float64=1.0`: Specified how much the solver should explore. In the UCB equation, Q + c*sqrt(log(t/N)), c is the exploration constant.
  * `n_iterations::Int64=100`: Number of iterations during each action() call.
  * `max_time::Float64`: Maximum amount of CPU time in seconds spent iterating through simulations.
  * Double progressive widening parameters. These constants control the double progressive widening. A new state   or action will be added if the number of children is less than or equal to kN^alpha.

      * `k_action::Float64=10`
      * `alpha_action::Float64=0.5`
      * `k_state::Float64=10`
      * `alpha_state::Float64=0.5`
  * `keep_tree::Bool=false`: If true, store the tree in the planner for reuse at the next timestep (and every time it is used in the future). There is a computational cost for maintaining the state dictionary necessary for this.
  * `enable_action_pw::Bool=true`: If true, enable progressive widening on the action space; if false just use the whole action space.
  * `enable_state_pw::Bool=true`: If true, enable progressive widening on the state space; if false just use the single next state (for deterministic problems).
  * `check_repeat_state::Bool=true`, `check_repeat_action::Bool=true`: When constructing the tree, check whether a state or action has been seen before (there is a computational cost to maintaining the dictionaries necessary for this)
  * `tree_in_info::Bool=false`: If true, return the tree in the info dict when action_info is called. False by default because it can use a lot of memory if histories are being saved.
  * `rng::AbstractRNG=Random.GLOBAL_RNG`: Random number generator
  * `estimate_value::Any=RolloutEstimator(RandomSolver(rng))`: (rollout policy) Function, object, or number used to estimate the value at the leaf nodes.

      * If this is a function `f`, `f(mdp, s, depth)` will be called to estimate the value (depth can be ignored).
      * If this is an object `o`, `estimate_value(o, mdp, s, depth)` will be called.
      * If this is a number, the value will be set to that number.
  * `init_Q::Any=0.0`: Function, object, or number used to set the initial Q(s,a) value at a new node.

      * If this is a function `f`, `f(mdp, s, a)` will be called to set the value.
      * If this is an object `o`, `init_Q(o, mdp, s, a)` will be called.
      * If this is a number, Q will always be set to that number.
  * `init_N::Any=0`: Function, object, or number used to set the initial N(s,a) value at a new node.

      * If this is a function `f`, `f(mdp, s, a)` will be called to set the value.
      * If this is an object `o`, `init_N(o, mdp, s, a)` will be called.
      * If this is a number, N will always be set to that number.
  * `next_action::Any=RandomActionGenerator(rng)`: Function or object used to choose the next action to be considered for progressive widening.  The next action is determined based on the MDP, the state, `s`, and the current `DPWStateNode`, `snode`.

      * If this is a function `f`, `f(mdp, s, snode)` will be called to set the value.
      * If this is an object `o`, `next_action(o, mdp, s, snode)` will be called.
  * `default_action::Any=ExceptionRethrow()`: Function, action, or Policy used to determine the action if POMCP fails with exception `ex`.

      * If this is a Function `f`, `f(pomdp, belief, ex)` will be called.
      * If this is a Policy `p`, `action(p, belief)` will be called.
      * If it is an object `a`, `default_action(a, pomdp, belief, ex)` will be called, and if this method is not implemented, `a` will be returned directly.
  * `reset_callback::Function=(mdp, s)->false`: Function used to reset/reinitialize the MDP to a given state `s`. Useful when the simulator state is not truly separate from the MDP state. `f(mdp, s)` will be called. By default, this will be optimized out by the compiler.
  * `show_progress::Bool=false` Show progress bar during simulation.
  * `timer::Function=()->1e-9*time_ns()`: Timekeeping method. Search iterations ended when `timer() - start_time ≥ max_time`.
