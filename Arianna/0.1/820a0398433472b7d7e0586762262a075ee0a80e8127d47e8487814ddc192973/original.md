```
abstract type Action
```

Abstract type representing Monte Carlo actions/moves that can be performed on a system.

Concrete subtypes must implement:

  * `sample_action!(action, policy, parameters, system, rng)`: Sample a new action from the policy
  * `perform_action!(system, action)`: Apply the action to modify the system state
  * `invert_action!(action, system)`: Invert/reverse the action
  * `log_proposal_density(action, policy, parameters, system)`: Log probability density of proposing this action

Optional methods:

  * `revert_action!(system, action)`: Optimized version of perform_action! that can reuse cached values
