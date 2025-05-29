`add_edges!(G,edge_table)` はグラフ `G` にエッジを追加します。引数 `edge_table` は追加されるエッジのイテラブルなリスト（配列または集合）です（2つのタプル）。グラフに追加されたエッジの数を返します。

これは `G` が `UndirectedGraph` の場合でも `DirectedGraph` の場合でも機能します。
