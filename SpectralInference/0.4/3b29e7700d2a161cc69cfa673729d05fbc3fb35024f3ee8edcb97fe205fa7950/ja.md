```
spectral_lineage_encoding(tree::Node, orderedleafnames=getleafnames(tree); filterfun=x->true)
```

は、ノードの `nodeid` と、`orderedleafnames` に従って順序付けられたブール値のベクトル `sle` を持つ名前付きタプルのベクトルを返します。ここで、true は葉がノードから降りていることを示し、false はそうでないことを示します。
