```
evaluate_and_jacobian!(u, U, F::PolynomialSystem, x, p)
```

システム `F` を `x` で評価し、パラメータ `p` を用いてそのヤコビ行列を計算し、結果を `u` (評価) と `U` (ヤコビ行列) に格納します。
