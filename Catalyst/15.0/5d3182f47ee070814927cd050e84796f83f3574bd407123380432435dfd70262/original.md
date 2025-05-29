```
reactions(network)
```

Given a [`ReactionSystem`](@ref), return a vector of all `Reactions` in the system.

Notes:

  * If `ModelingToolkit.get_systems(network)` is not empty, will allocate.
