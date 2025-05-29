```
trees(b::Booster; with_stats=true)
```

Return all trees of the model of the `Booster` `b` as [`Node`](@ref) objects.  The output of this function is a `Vector` of `Node`s each representing the root of a separate tree.

If `with_stats` the output `Node` objects will contain the computed statistics `gain` and `cover`.
