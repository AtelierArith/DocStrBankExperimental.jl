```
 ValuePolicy{P<:Union{POMDP,MDP}, T<:AbstractMatrix{Float64}, A}
```

A generic MDP policy that consists of a value table. The entry at `stateindex(mdp, s)` is the action that will be taken in state `s`. It is expected that the order of the actions in the value table is consistent with the order of the actions in `act`.  If `act` is not explicitly set in the construction, `act` is ordered according to `actionindex`.

# Fields

  * `mdp::P` the MDP problem
  * `value_table::T` the value table as a |S|x|A| matrix
  * `act::Vector{A}` the possible actions
