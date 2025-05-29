```
VectorPolicy{S,A}
```

A generic MDP policy that consists of a vector of actions. The entry at `stateindex(mdp, s)` is the action that will be taken in state `s`.

# Fields

  * `mdp::MDP{S,A}` the MDP problem
  * `act::Vector{A}` a vector of size |S| mapping state indices to actions
