```
degree(g::GNNHeteroGraph, edge_type::EType; dir = :in)
```

`g` GNNHeteroGraph における `edge_type` に基づいてノードの次数を含むベクトルを返します。

# 引数

  * `g`: グラフ。
  * `edge_type`: エッジタイプを表すシンボルのタプル `(source_t, edge_t, target_t)`。
  * `T`: 返されるベクトルの要素タイプ。`nothing` の場合、グラフタイプに基づいて選択されます。デフォルトは `nothing`。
  * `dir`: `dir = :out` の場合、ノードの次数は出力エッジに基づいてカウントされます。`dir = :in` の場合、入力エッジが使用されます。`dir = :both` の場合、両方の合計が得られます。デフォルトは `dir = :out`。
