```
rpmatli(p::Int, nlv::Int, Q = Float64; s)
```

スパースなランダム射影行列を構築します（Achlioptas 2001, Li et al. 2006）。

  * `p` : 射影する変数（属性）の数。
  * `nlv` : シミュレーションされた射影次元の数。
  * `Q` : 構築された射影行列の成分の型。

キーワード引数:

  * `s` : 返される行列のスパース性を定義する係数（`s` が大きいほど、スパース性が高くなる）。

この関数は、次元 `p` x `nlv` のランダム射影行列 V を返します。サイズ n x `p` の与えられた行列 X の射影は、X * V で与えられます。

行列 V は、以下の値の中から独立同分布の離散サンプリングによってシミュレートされます：

  * 確率 1/(2 * `s`) で 1
  * 確率 1 - 1 / `s` で 0
  * 確率 1/(2 * `s`) で -1

`s` の通常の値は次の通りです：

  * sqrt(`p`)       (Li et al. 2006)
  * `p` / log(`p`)  (Li et al. 2006)
  * 1               (Achlioptas 2001)
  * 3               (Achlioptas 2001)

## 参考文献

Achlioptas, D., 2001. Database-friendly random projections,  in: Proceedings of the Twentieth ACM SIGMOD-SIGACT-SIGART  Symposium on Principles of Database Systems, PODS ’01.  Association for Computing Machinery, New York, NY, USA, pp. 274–281.  https://doi.org/10.1145/375551.375608

Li, V., Hastie, T.J., Church, K.W., 2006. Very sparse random  projections, in: Proceedings of the 12th ACM SIGKDD International  Conference on Knowledge Discovery and Data Mining, KDD ’06. Association  for Computing Machinery, New York, NY, USA, pp. 287–296.  https://doi.org/10.1145/1150402.1150436

## 例

```julia
using Jchemo
p = 10 ; nlv = 3
rpmatli(p, nlv)
```
