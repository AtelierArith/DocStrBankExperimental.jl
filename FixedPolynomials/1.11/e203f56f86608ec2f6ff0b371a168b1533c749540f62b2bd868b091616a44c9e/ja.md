```
evaluate_and_jacobian!(u, U, F, x, cfg::JacobianConfig)
```

`F` とそのヤコビアンを `x` で評価し、`cfg` にある事前計算された値を使用して結果を `u` と `U`（ヤコビアン）に格納します。

### 例

```julia
evaluate_and_jacobian!(u, U, F, x, config(F, x))
```
