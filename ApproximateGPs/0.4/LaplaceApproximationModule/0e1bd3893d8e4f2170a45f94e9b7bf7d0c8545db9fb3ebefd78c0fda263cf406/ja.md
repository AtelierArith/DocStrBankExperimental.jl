```
posterior(la::LaplaceApproximation, lfx::LatentFiniteGP, ys)
```

ラプラス近似を使用して、事後分布 `p(f | y)` に対するガウス近似 `q(f)` を構築します。ニュートン法を使用して事後分布のモードを解決します。
