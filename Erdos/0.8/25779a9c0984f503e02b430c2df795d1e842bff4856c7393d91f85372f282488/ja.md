```
random_regular_graph(n::Int, k::Int, G=Graph; seed=-1)
```

`n` 頂点を持ち、各頂点の次数が `k` のランダム無向 [正則グラフ](https://en.wikipedia.org/wiki/Regular_graph) を作成します。

無向グラフの場合、`nk` 個の `Int` の配列を割り当て、約 $nk^2$ 時間を要します。$k > n/2$ の場合、次数が `n-k-1` のグラフを生成し、その補グラフを返します。

`G` は結果のグラフの型です。
