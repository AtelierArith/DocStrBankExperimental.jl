```
add_edges(g::GNNHeteroGraph, edge_t, s, t; [edata, num_nodes])
add_edges(g::GNNHeteroGraph, edge_t => (s, t); [edata, num_nodes])
add_edges(g::GNNHeteroGraph, edge_t => (s, t, w); [edata, num_nodes])
```

ヘテログラフ `g` に、ソースノードベクター `s` とターゲットノードベクター `t` を持つエッジタイプ `edge_t` のエッジを追加します。オプションで、新しいエッジのエッジウェイト `w` または特徴 `edata` を渡すことができます。`edge_t` はシンボルの三つ組 `(src_t, rel_t, dst_t)` です。

エッジタイプがグラフに既に存在しない場合は追加されます。新しいノードタイプが関与している場合、それらもグラフに追加されます。この場合、`num_nodes` の辞書または名前付きタプルを渡して新しいタイプのノードの数を指定できます。そうでない場合、ノードの数は `s` と `t` の最大ノードIDから推測されます。
