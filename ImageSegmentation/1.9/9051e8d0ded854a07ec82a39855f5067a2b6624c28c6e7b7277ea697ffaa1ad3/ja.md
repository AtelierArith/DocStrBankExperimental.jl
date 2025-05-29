```
G, vert_map = region_adjacency_graph(seg, weight_fn)
```

`SegmentedImage`から領域隣接グラフ（RAG）を構築します。RAGとDict(label=>vertex)マップを返します。`weight_fn`はエッジに重みを割り当てるために使用されます。

```
weight_fn(label1, label2)
```

label1とlabel2の間のエッジの重みに対応する実数を返します。
