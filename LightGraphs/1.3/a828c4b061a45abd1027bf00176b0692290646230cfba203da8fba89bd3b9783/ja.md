```
greedy_color(g; sort_degree=false, reps = 1)
```

グラフ `g` に基づいて [貪欲彩色ヒューリスティック](https://en.wikipedia.org/wiki/Greedy_coloring) で色を付けます。

ヒューリスティックは、頂点の順列を選択し、その順序で利用可能な最小の色インデックスを反復的に割り当てることとして説明できます。

`sort_degree` が true の場合、順列は頂点の次数の逆ソート順で選択されます。この場合、`parallel` と `reps` は無関係です。

`sort_degree` が false の場合、`reps` 回の彩色がランダムな順列に基づいて得られ、最も少ない色を使用するものが選択されます。
