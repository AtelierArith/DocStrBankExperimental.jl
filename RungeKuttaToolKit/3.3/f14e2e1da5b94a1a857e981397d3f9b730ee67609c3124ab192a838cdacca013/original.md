```
RKOCEvaluatorMFV{S,T,N}(
    trees::AbstractVector{LevelSequence},
) -> RKOCEvaluatorMFV{S,T,N}
```

Construct an `RKOCEvaluatorMFV` that encodes a given list of rooted trees.

Unlike a standard `RKOCEvaluator`, the number of stages `S` is provided as a static type parameter in order to statically determine the SIMD vector width.

# Arguments

  * `trees`: input list of rooted trees in `LevelSequence` representation.

If the type `T` is not specified, it defaults to `Float64`.
