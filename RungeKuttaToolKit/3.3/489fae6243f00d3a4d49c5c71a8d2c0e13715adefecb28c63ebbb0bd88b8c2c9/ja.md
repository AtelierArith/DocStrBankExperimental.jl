```
RKOCEvaluatorMFV{S,T,N}(order::Integer) -> RKOCEvaluatorMFV{S,T,N}
```

`order` 頂点を持つすべての根付き木をエンコードする `RKOCEvaluatorMFV` を構築します。これは `RKOCEvaluatorMFV{S,T}(all_rooted_trees(order))` と同等です。

標準の `RKOCEvaluator` と異なり、ステージの数 `S` は SIMD ベクトル幅を静的に決定するために静的型パラメータとして提供されます。

型 `T` が指定されていない場合、デフォルトは `Float64` です。
