```
node_mtg(node::Node)
```

ノードのMTGエンコーディングを取得します。*すなわち* MTGの説明（[`NodeMTG`](@ref)または[`MutableNodeMTG`](@ref)を参照）：

  * `scale`: ノードのスケール（*例* 1）
  * `symbol`: ノードのシンボル（*例* "Axis"）
  * `index`: ノードのインデックス（*例* 1、これは自由です）
  * `link`: ノードのリンク ("/", "+" または "<")
