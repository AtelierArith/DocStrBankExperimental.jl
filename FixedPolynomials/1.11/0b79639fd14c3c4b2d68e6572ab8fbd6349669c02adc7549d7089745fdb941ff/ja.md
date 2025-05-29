```
jacobian(u, F, x, cfg::JacobianConfig [, precomputed=false])
```

`F`の`x`におけるヤコビアンを、`cfg`の事前計算された値を使用して評価します。返される行列は`similar(x, T, m, n)`を使用して構築されます。

### 例

```julia
cfg = JacobianConfig(F)
jacobian(F, x, cfg)
```

`precomputed=true`の場合、`cfg`内の以前の中間結果に依存します。したがって、結果は、同じ`x`で`evaluate`または`jacobian`を事前に呼び出した場合にのみ正しいです。
