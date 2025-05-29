```
graph=merge_graphs(
graph1,
graph2;
prefix1 = "",
prefix2 = "G2",
skip_basic1 = true,
skip_basic2 = true,
cref1 = Vector(),
cref2 = Vector(),
input1 = :A,
input2 = :A,
```

)

Takes all the nodes and edges in `graph1` and `graph2` and generates a new graph. The node names are in `graph1` are changed by adding a prefix `prefix1` and `graph2` correspondingly. The nodes `:I` and `:A` are unchanged if `skip_basicX=true`. All coefficient references `crefX` are modified accordingly.
