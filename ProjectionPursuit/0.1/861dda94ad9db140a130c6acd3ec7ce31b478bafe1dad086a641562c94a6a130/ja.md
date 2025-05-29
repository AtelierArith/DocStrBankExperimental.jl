```
gensphere(N::Int64, d::Int64)
```

次元 d の単位球上で長さ N の低差異列を生成します。

ざっくり言うと、低差異列とは、確率変数のサンプルの列であり、領域内の点の数が領域の大きさに比例する特性を持っています。

この関数は、各行が d 次元単位球上で一様に分布するランダムベクトルのサンプルを表す N 行 d 列の行列を返します。

Brauchart, Johann S., Josef Dick, and Lou Fang. "Spatial low-discrepancy sequences, spherical cone discrepancy, and applications in financial modeling." Journal of Computational and Applied Mathematics 286 (2015): 28-53.
