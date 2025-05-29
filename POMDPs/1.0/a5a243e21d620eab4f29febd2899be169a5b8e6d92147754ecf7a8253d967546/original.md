```
history(b)
```

Return the action-observation history associated with belief `b`.

The history should be an `AbstractVector`, `Tuple`, (or similar object that supports indexing with `end`) full of `NamedTuples` with keys `:a` and `:o`, i.e. `history(b)[end][:a]` should be the last action taken leading up to `b`, and `history(b)[end][:o]` should be the last observation received.

It is acceptable to return only part of the history if that is all that is available, but it should always end with the current observation. For example, it would be acceptable to return a structure containing only the last three observations in a length 3 `Vector{NamedTuple{(:o,),Tuple{O}}`.
