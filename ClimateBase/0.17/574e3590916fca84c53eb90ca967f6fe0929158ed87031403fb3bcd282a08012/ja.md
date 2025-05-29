```
missing_weights(A::ClimArray, val = missing_val(A)) → B, W
```

新しい配列 `B` を生成します。`B` の値は `A` と同じですが、`A` の `missing` 値は `val` で置き換えられます。また、重みの配列も生成され、`A` に `missing` があった場合は値が 0 になり、そうでない場合は値が 1 になります。

この関数の出力は、データに `missing` 値があり、集約プロセス中にそれらを *完全にスキップ* したい場合に、`spacemean, timemean, ...` などの ClimateBase.jl の集約関数と一緒に使用する必要があります。

この関数は、`A` に `missing` 値がない場合、`A, nothing` を返します。
