```
rollout!(::Problem)
```

初期条件 `x0` から制御 `Z` に沿って動的シミュレーションを行います。問題が渡された場合、`Z = prob.Z`、`model = prob.model`、および `x0 = prob.x0` となります。
