`twins(G,u,v)` は `u` と `v` が `G` の双子頂点であるかどうかを判断します。つまり、`G[u]-v == G[v]-u` であるかどうかです。これは同値関係です。

`twins(G)` はグラフの頂点集合を双子同値類に分割して返します。
