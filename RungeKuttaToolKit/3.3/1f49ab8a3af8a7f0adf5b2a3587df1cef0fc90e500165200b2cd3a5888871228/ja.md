```
RKOCEvaluator{T}(order::Integer, num_stages::Integer) -> RKOCEvaluator{T}
```

最大 `order` 頂点を持つすべての根付き木をエンコードする `RKOCEvaluator` を構築します。これは `RKOCEvaluator{T}(all_rooted_trees(order), num_stages)` と同等です。

型 `T` が指定されていない場合、デフォルトは `Float64` です。
