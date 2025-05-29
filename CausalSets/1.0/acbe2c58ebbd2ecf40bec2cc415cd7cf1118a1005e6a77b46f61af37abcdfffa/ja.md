```
bd_chain_coef_along(causet, chain, dim, dim, locality locality[, max_cardinality]) -> Float64
```

チェーン `chain` のためのベニンカサ-ダウカー連鎖係数を `causet` で返します。すなわち、チェーンのステップ間の個々の BD 係数の積です。もし `chain` がチェーンでない場合は `0` を返します。
