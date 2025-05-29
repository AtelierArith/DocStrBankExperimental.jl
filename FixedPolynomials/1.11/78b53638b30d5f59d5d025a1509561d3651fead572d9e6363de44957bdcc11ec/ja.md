```
jacobian!(u, F, x, cfg::JacobianConfig [, precomputed=false])
```

`F`の`x`におけるヤコビアンを評価し、`cfg`の事前計算された値を使用して結果を`u`に格納します。

### 例

```julia
cfg = JacobianConfig(F)
jacobian!(u, F, x, cfg)
```

`precomputed=true`の場合、`cfg`内の以前の中間結果に依存します。したがって、結果は、同じ`x`で`evaluate`または`jacobian`を以前に呼び出した場合にのみ正しいです。
