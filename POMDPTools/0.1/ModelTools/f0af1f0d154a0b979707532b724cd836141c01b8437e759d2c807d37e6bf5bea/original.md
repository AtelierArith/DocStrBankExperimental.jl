```
ordered_states(mdp)
```

Return an `AbstractVector` of states ordered according to `stateindex(mdp, a)`.

`ordered_states(mdp)` will always return a `AbstractVector{A}` `v` containing all of the states in `states(mdp)` in the order such that `stateindex(mdp, v[i]) == i`. You may wish to override this for your problem for efficiency.
