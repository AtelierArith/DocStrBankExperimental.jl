```
unconstrained_nls(solver; problem_set = unconstrained_nls_set(), atol = 1e-6, rtol = 1e-6)
```

`solver`を制約のない非線形最小二乗問題でテストします。`rtol`がゼロでない場合、相対誤差は初期推定値での勾配を使用します。
