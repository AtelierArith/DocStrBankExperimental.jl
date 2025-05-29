```
POMCPSolver(#=keyword arguments=#)
```

Partially Observable Monte Carlo Planning Solver.

## Keyword Arguments

  * `max_depth::Int`   Rollouts and tree expension will stop when this depth is reached.   default: `20`
  * `c::Float64`   UCB exploration constant - specifies how much the solver should explore.   default: `1.0`
  * `tree_queries::Int`   Number of iterations during each action() call.   default: `1000`
  * `max_time::Float64`   Maximum time for planning in each action() call.   default: `Inf`
  * `tree_in_info::Bool`   If `true`, returns the tree in the info dict when action_info is called.   default: `false`
  * `estimate_value::Any`   Function, object, or number used to estimate the value at the leaf nodes.   default: `RolloutEstimator(RandomSolver(rng))`

      * If this is a function `f`, `f(pomdp, s, h::BeliefNode, steps)` will be called to estimate the value.
      * If this is an object `o`, `estimate_value(o, pomdp, s, h::BeliefNode, steps)` will be called.
      * If this is a number, the value will be set to that number

    Note: In many cases, the simplest way to estimate the value is to do a rollout on the fully observable MDP with a policy that is a function of the state. To do this, use `FORollout(policy)`.
  * `default_action::Any`   Function, action, or Policy used to determine the action if POMCP fails with exception `ex`.   default: `ExceptionRethrow()`

      * If this is a Function `f`, `f(pomdp, belief, ex)` will be called.
      * If this is a Policy `p`, `action(p, belief)` will be called.
      * If it is an object `a`, `default_action(a, pomdp, belief, ex)` will be called, and if this method is not implemented, `a` will be returned directly.
  * `time::Function`   Function to call to get the time in seconds. This is used to check if the maximum time has been reached.   default: `() -> time_ns()*1e-9`
  * `rng::AbstractRNG`   Random number generator.   default: `Random.GLOBAL_RNG`
