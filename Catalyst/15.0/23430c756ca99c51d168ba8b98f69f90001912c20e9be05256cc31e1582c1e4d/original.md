```
ModelingToolkit.flatten(rs::ReactionSystem)
```

Merges all subsystems of the given [`ReactionSystem`](@ref) up into `rs`.

Notes:

  * Returns a new `ReactionSystem` that represents the flattened system.
  * All `Reaction`s within subsystems are namespaced and merged into the list of `Reactions` of `rs`. The merged list is then available as `reactions(rs)`.
  * All algebraic and differential equations are merged in the equations of `rs`.
  * Currently only `ReactionSystem`s, `NonlinearSystem`s and `ODESystem`s are supported as sub-systems when flattening.
  * `rs.networkproperties` is reset upon flattening.
  * The default value of `combinatoric_ratelaws` will be the logical or of all `ReactionSystem`s.
