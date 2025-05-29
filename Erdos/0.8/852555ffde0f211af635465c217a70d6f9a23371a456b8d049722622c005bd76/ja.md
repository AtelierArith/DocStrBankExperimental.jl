```
random_regular_digraph(n::Int, k::Int; dir::Symbol=:out, seed=-1)
```

`n` 頂点を持ち、各頂点の次数が `k` のランダム有向 [正則グラフ](https://en.wikipedia.org/wiki/Regular_graph) を作成します。次数（入次数または出次数）は `dir=:in` または `dir=:out` を使用して指定できます。

有向グラフの場合、隣接行列としてブール値の $n \times n$ スパース行列を割り当て、それを使用してグラフを生成します。
