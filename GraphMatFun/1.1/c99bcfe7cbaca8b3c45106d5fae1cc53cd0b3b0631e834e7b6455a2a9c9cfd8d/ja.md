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

`graph1`と`graph2`のすべてのノードとエッジを取り込み、新しいグラフを生成します。ノード名は`graph1`では`prefix1`を追加することで変更され、`graph2`も同様です。ノード`:I`と`:A`は`skip_basicX=true`の場合は変更されません。すべての係数参照`crefX`はそれに応じて修正されます。
