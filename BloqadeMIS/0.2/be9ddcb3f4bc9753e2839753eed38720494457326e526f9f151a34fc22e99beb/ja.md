```
to_independent_set!(config::AbstractVector, graph::AbstractGraph)
```

`config`にある頂点を排除して、残りの頂点が接続されたエッジを持たないようにします。このアルゴリズムは、必ずしも最大の頂点集合を与えるわけではない単純な頂点排除です。

```@example
# 以下のコードをAtom/VSCodeで実行します
atoms = [(0.0, 1.0), (1.0, 0.), (2.0, 0.0), (1.0, 1.0), (1.0, 2.0), (2.0, 2.0)]
graph = unit_disk_graph(atoms, 1.5)

config = [1, 1, 1, 0, 1, 1]
viz_config(atoms, graph, config)

to_independent_set!(config, graph)
viz_config(atoms, graph, config)
```
