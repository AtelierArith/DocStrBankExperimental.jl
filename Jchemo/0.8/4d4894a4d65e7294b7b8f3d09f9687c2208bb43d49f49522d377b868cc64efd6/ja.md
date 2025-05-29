```
rpmatgauss(p::Int, nlv::Int, Q = Float64)
```

ガウスランダム射影行列を構築します。

  * `p` : 射影する変数（属性）の数。
  * `nlv` : シミュレーションされた射影次元の数。
  * `Q` : 構築された射影行列の成分の型。

この関数は、次元 `p` x `nlv` のランダム射影行列 V を返します。サイズ n x `p` の与えられた行列 X の射影は X * V で与えられます。

V は i.i.d. N(0, 1) / sqrt(`nlv`) からシミュレーションされます。

## 参考文献

Li, V., Hastie, T.J., Church, K.W., 2006. 非常にスパースなランダム射影, in: Proceedings of the 12th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, KDD ’06. Association for Computing Machinery, New York, NY, USA, pp. 287–296. https://doi.org/10.1145/1150402.1150436

## 例

```julia
using Jchemo
p = 10 ; nlv = 3
rpmatgauss(p, nlv)
```
