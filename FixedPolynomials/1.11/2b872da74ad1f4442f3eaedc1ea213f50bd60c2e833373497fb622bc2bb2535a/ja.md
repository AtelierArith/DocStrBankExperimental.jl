```
evaluate(g, x, cfg::GradientConfig [, precomputed=false])
```

`g`を`x`で評価し、`cfg`の事前計算された値を使用します。これは通常、`evaluate(g, x)`よりもかなり速いです。

### 例

```julia
cfg = GradientConfig(g)
evaluate(g, x, cfg)
```

`precomputed=true`の場合、`cfg`の以前の中間結果に依存します。したがって、結果は、同じ`x`で`evaluate`または`gradient`を事前に呼び出した場合にのみ正しいです。
