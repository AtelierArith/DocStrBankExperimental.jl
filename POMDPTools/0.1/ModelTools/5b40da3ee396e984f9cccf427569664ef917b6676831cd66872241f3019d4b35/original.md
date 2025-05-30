```
ordered_actions(mdp)
```

Return an `AbstractVector` of actions ordered according to `actionindex(mdp, a)`.

`ordered_actions(mdp)` will always return an `AbstractVector{A}` `v` containing all of the actions in `actions(mdp)` in the order such that `actionindex(mdp, v[i]) == i`. You may wish to override this for your problem for efficiency.
