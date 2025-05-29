```
loglikelihood(rbm, x)
loglikelihood(rbm, x, logz)
```

与えられたデータセット `x` に対する RBM の平均対数尤度を計算します。`logz` を分配関数の対数の値として使用するか、アニーリング重要サンプリングを用いて分配関数を推定します。
