```
Move{A<:Action,P<:Policy,V<:AbstractArray,T<:AbstractFloat}
```

A struct representing a Monte Carlo move with an associated action, policy, and parameters.

# Fields

  * `action::A`: The action to be performed in the move
  * `policy::P`: The policy used to propose actions
  * `parameters::V`: Parameters of the policy
  * `weight::T`: Weight/probability of selecting this move in a sweep
  * `total_calls::Int`: Total number of times this move has been attempted
  * `accepted_calls::Int`: Number of times this move has been accepted

# Type Parameters

  * `A`: Type of the action
  * `P`: Type of the policy
  * `V`: Type of the parameter array
  * `T`: Type of the weight (floating point)
