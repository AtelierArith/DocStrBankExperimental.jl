```
conf = GradientDescent(step_size_init, step_size_beta)
```

確率的勾配降下更新の設定で、ステップサイズは `(t::Int) -> step_size_init * (step_size_beta + 1) / (step_size_beta + t)` で与えられ、ここで `t` は反復回数です。
