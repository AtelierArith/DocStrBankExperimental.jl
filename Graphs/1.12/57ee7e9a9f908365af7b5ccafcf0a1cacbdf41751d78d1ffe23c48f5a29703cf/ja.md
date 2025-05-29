```
dag_longest_path(g, distmx=weights(g); topological_order=topological_sort_by_dfs(g))
```

有向非巡回グラフ `g` 内の最長パスを返し、距離行列 `distmx` を使用し、頂点を反復するために `topological_order` を使用します。
