```
ModelingToolkit.compose(sys::ReactionSystem, systems::AbstractArray; name = nameof(sys))
```

Compose the indicated [`ReactionSystem`](@ref) with one or more `AbstractSystem`s.

Notes:

  * The `AbstractSystem` being added in must be an `ODESystem`, `NonlinearSystem`, or `ReactionSystem` currently.
  * Returns a new `ReactionSystem` and does not modify `rs`.
  * By default, the new `ReactionSystem` will have the same name as `sys`.
