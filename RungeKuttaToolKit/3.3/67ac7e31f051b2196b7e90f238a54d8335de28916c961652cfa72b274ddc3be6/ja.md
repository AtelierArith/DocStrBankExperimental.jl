```
RKOCEvaluatorSIMD{S,T}(order::Integer) -> RKOCEvaluatorSIMD{S,T}
```

`order` 頂点を持つすべての根付き木をエンコードする `RKOCEvaluatorSIMD` を構築します。これは `RKOCEvaluatorSIMD{S,T}(all_rooted_trees(order))` と同等です。

標準の `RKOCEvaluator` と異なり、ステージの数 `S` は静的型パラメータとして提供され、SIMD ベクタ幅を静的に決定します。

型 `T` が指定されていない場合、デフォルトは `Float64` です。
