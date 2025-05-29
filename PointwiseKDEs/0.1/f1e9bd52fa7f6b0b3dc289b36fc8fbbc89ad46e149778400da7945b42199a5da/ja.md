```
PointwiseKDE(points::Matrix{T <: Real})
```

与えられたポイントの行列からガウスKDEを構築します。

`points`はサイズ`(ndim, npts)`である必要があります。バンド幅の選択はスコットのルールに従います。

結果は`rand`や`logpdf`などで使用するのに適した`MultivariateDistribution`オブジェクトです。
