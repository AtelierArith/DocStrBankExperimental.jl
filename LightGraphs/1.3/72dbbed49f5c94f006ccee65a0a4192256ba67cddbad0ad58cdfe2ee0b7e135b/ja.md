```
bfs_tree(g, s[; dir=:out])
```

グラフ `g` の幅優先探索を行い、始点頂点 `s` から探索を開始します。発見された順に頂点の有向非巡回グラフを返します。`dir` が指定されている場合は、対応する辺の方向を使用します（`:in` と `:out` が許容される値です）。
