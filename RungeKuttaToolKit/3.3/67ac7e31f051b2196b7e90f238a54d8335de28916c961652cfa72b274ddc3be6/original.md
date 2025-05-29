```
RKOCEvaluatorSIMD{S,T}(order::Integer) -> RKOCEvaluatorSIMD{S,T}
```

Construct an `RKOCEvaluatorSIMD` that encodes all rooted trees having at most `order` vertices. This is equivalent to `RKOCEvaluatorSIMD{S,T}(all_rooted_trees(order))`.

Unlike a standard `RKOCEvaluator`, the number of stages `S` is provided as a static type parameter in order to statically determine the SIMD vector width.

If the type `T` is not specified, it defaults to `Float64`.
