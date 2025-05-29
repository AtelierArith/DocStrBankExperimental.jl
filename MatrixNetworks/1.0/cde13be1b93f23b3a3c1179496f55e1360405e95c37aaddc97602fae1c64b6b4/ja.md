# `roach_graph`

4n 頂点のローチグラフを生成します。このグラフは Guattery-Miller の説明に従います。ローチグラフの本体は 2n 頂点からなり、2 つの n 頂点のライングラフが接続されています。本体には、各側の 1 つの頂点に n 頂点のライングラフを追加することによって生じる 2 つのアンテナがあります。

```
# グラフは次のようになります
#
# (           上部本体               )   (       上部アンテナ       )    
#
# o - o - o - ... 合計 n 頂点 - o - o - ... 合計 n 頂点 - 0
# |   |   |   ...    |   |   |   |   |
# o - o - o - ... 合計 n 頂点 - o - o - ... 合計 n 頂点 - 0
#
# (         下部本体              )   (     下部アンテナ      )
#
# 頂点は 4n あり、辺は 2(2n-1) + n です
```

## 関数

  * `roach_graph(n) -> A::MatrixNetwork`
  * `roach_graph(n, Val{true}) -> (A::MatrixNetwork, Matrix{Float64})` これはグラフの座標も返します。

## 例

```
A = sparse_transpose(roach_graph(3, Val{true})) # 行列を取得
L = spdiagm(vec(sum(A,2))) - A

#lams,vecs = eig(full(L))

```
