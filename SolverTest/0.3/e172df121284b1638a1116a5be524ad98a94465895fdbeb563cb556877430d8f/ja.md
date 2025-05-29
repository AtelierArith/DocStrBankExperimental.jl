```
unconstrained_nlp(solver; problem_set = unconstrained_nlp_set(), atol = 1e-6, rtol = 1e-6)
```

`solver`を制約のない問題でテストします。`rtol`がゼロでない場合、相対誤差は初期推定値での勾配を使用します。
