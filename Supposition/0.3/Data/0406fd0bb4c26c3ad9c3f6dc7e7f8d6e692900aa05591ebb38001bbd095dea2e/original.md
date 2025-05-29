```
produce!(tc::TestCase, pos::Possibility{T}) -> T
```

Produces a value from the given `Possibility`, recording the required choices in the `TestCase` `tc`.

This needs to be implemented for custom `Possibility` objects, passing the given `tc` to any inner requirements directly.

See also [`Supposition.produce!`](@ref)

!!! tip "Examples"
    You should not call this function when you have a `Possibility` and want to inspect what an object produced by that `Possibility` looks like - use [`example`](@ref) for that instead.

