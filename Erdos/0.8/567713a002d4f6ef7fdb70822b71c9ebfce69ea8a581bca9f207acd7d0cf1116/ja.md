```
a_star(g, s, t, distmx=weights(g), heuristic = n->0)
```

頂点 `s` と `t` の間の最短経路を [A* 探索アルゴリズム](http://en.wikipedia.org/wiki/A%2A_search_algorithm) を使用して計算します。オプションのヒューリスティック関数とエッジ距離行列を指定することができます。経路が存在しない場合は空の経路を返します。
