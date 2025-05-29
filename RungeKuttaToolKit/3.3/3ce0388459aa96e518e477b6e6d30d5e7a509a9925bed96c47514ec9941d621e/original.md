```
RKOCEvaluatorSIMD{S,T}(
    trees::AbstractVector{LevelSequence},
) -> RKOCEvaluatorSIMD{S,T}
```

Construct an `RKOCEvaluatorSIMD` that encodes a given list of rooted trees.

Unlike a standard `RKOCEvaluator`, the number of stages `S` is provided as a static type parameter in order to statically determine the SIMD vector width.

# Arguments

  * `trees`: input list of rooted trees in `LevelSequence` representation.

If the type `T` is not specified, it defaults to `Float64`.
