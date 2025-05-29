```
TimeDerivative(p::Process [, τ])
```

既存のプロセスを時間微分に変換するには、`τ * Differential(t)(LHS(p)) ~ RHS(p)`を作成します。
