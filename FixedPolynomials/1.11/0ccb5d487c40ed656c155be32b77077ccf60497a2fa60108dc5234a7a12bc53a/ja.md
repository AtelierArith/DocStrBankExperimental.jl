```
gradient!(u, g, x, cfg::GradientConfig [, precomputed=false])
```

`g`の`x`における勾配を計算し、結果を`u`に格納します。`cfg`にある事前計算された値を使用します。

### 例

```julia
cfg = GradientConfig(g)
gradient(u, g, x, cfg)
```

`precomputed=true`の場合、`cfg`にある以前の中間結果に依存します。したがって、結果は、以前に同じ`x`で`evaluate`または`gradient`を呼び出した場合にのみ正しいです。
