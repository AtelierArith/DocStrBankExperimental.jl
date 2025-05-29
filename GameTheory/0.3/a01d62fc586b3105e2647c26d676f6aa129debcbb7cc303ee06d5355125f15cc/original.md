```
pure2mixed(num_actions, action)
```

Convert a pure action to the corresponding mixed action.

# Arguments

  * `num_actions::Integer` : The number of the pure actions (= the length of a mixed action).
  * `action::PureAction` : The pure action to convert to the corresponding mixed action.

# Returns

  * `mixed_action::Vector{Float64}` : The mixed action representation of the given pure action.
