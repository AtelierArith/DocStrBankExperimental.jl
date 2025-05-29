```
floyd_warshall_shortest_paths(g, distmx=weights(g))
```

グラフ `g` のすべての頂点間の最短経路を計算するために[Floyd-Warshallアルゴリズム](http://en.wikipedia.org/wiki/Floyd–Warshall_algorithm)を使用します。関連するトラバーサル情報を持つ `FloydWarshallState` を返し、各頂点はグラフ内の各頂点に対するメトリックを含むベクトルのベクトルとしてインデックス付けされています。

このアルゴリズムは大量のデータを返す可能性があることに注意してください（$O(nv^2)$のオーダーでメモリを割り当てます）。
