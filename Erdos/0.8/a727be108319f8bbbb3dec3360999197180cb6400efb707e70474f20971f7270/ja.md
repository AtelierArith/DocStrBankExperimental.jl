```
betweenness_centrality(g; normalize=true, endpoints=false, approx=-1)
```

グラフ `g` の頂点の [媒介中心性](https://en.wikipedia.org/wiki/Centrality#Betweenness_centrality) を計算します。

頂点 `v` の媒介中心性は次のように定義されます：

$$
bc(v) = \frac{1}{\mathcal{N}} \sum_{s \neq t \neq v}
        \frac{\sigma_{st}(v)}{\sigma_{st}},
$$

ここで、$\sigma _{st}} \sigma_{st}$ はノード `s` からノード `t` への最短経路の総数であり、$\sigma_{st}(v)$ は `v` を通過する経路の数です。

`endpoints=true` の場合、エンドポイントは最短経路のカウントに含まれます。

`normalize=true` の場合、媒介中心性の値はグラフ内のすべてのペア間の可能な異なる経路の総数で正規化されます。無向グラフの場合、この数は `((n-1)*(n-2))/2` であり、有向グラフの場合は `(n-1)*(n-2)` で、ここで `n` はグラフ内の頂点の数です。

整数引数 `approx > 0` が指定された場合、`approx` 個のランダムに選ばれた頂点を含むグラフの各頂点の媒介中心性の近似値を返します。

**参考文献**

[1] Brandes 2001 & Brandes 2008 ```
