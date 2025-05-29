```
isconstant(A)
isconstant(A::PeriodicFunctionMatrix; check_const = false, atol = 1000*eps(), rtol = sqrt(eps()) )
```

周期行列の定数性チェック。周期関数行列 `A(t)` に対して、オプションの最適化に基づく定数性チェックを `check_const = true` を使用して実行することができ、絶対許容誤差 `atol` と相対許容誤差 `rtol` をそれぞれ指定します。
