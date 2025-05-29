```
RKOCEvaluator{T}(order::Integer, num_stages::Integer) -> RKOCEvaluator{T}
```

Construct an `RKOCEvaluator` that encodes all rooted trees having at most `order` vertices. This is equivalent to `RKOCEvaluator{T}(all_rooted_trees(order), num_stages)`.

If the type `T` is not specified, it defaults to `Float64`.
