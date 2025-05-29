```
ModelingToolkit.extend(sys::AbstractSystem, rs::ReactionSystem; name::Symbol=nameof(sys))
```

Extends the indicated [`ReactionSystem`](@ref) with another `AbstractSystem`.

Notes:

  * The `AbstractSystem` being added in must be an `ODESystem`, `NonlinearSystem`, or `ReactionSystem` currently.
  * Returns a new `ReactionSystem` and does not modify `rs`.
  * By default, the new `ReactionSystem` will have the same name as `sys`.
