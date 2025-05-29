```
evaluate(F, x, cfg::JacobianConfig [, precomputed=false])
```

システム `F` を `x` で評価し、`cfg` の事前計算された値を使用します。これは通常、`map(f -> evaluate(f, x), F)` よりもかなり速いです。返されるベクトルは `similar(x, T)` を使用して構築されます。

### 例

```julia
cfg = JacobianConfig(F)
evaluate(F, x, cfg)
```

`precomputed=true` の場合、`cfg` の以前の中間結果に依存します。したがって、結果は、同じ `x` で `evaluate` または `jacobian` を事前に呼び出した場合にのみ正しいです。
