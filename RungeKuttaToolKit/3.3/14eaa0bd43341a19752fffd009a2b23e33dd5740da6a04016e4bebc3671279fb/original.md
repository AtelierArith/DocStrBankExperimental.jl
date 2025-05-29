```
RKOCEvaluator{T}(
    trees::AbstractVector{LevelSequence},
    num_stages::Integer,
) -> RKOCEvaluator{T}
```

Construct an `RKOCEvaluator` that encodes a given list of rooted trees.

# Arguments

  * `trees`: input list of rooted trees in `LevelSequence` representation.
  * `num_stages`: number of stages (i.e., size of the Butcher tableau). Must be   specified at construction time to allocate internal workspace arrays.

If the type `T` is not specified, it defaults to `Float64`.
