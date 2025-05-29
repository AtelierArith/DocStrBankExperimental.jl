```
equality_constrained_nls(solver; problem_set = equality_constrained_nls_set(), atol = 1e-6, rtol = 1e-6)
```

`solver`を等式制約付き問題でテストします。`rtol`がゼロでない場合、相対誤差は初期推定値での勾配を使用します。
