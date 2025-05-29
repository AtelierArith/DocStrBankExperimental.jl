```
exactloglikelihood(rbm, x)
```

与えられたデータセット `x` と RBM `rbm` のための平均対数尤度を正確に計算します。分配関数の対数は `exactlogpartitionfunction(rbm)` によって正確に計算されます。それに加えて、この関数は単に `loglikelihood(rbm, x)` を呼び出します。
