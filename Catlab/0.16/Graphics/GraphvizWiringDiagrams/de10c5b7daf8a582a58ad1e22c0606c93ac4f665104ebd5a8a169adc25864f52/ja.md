Graphvizを使用して円形ポートグラフを描画します。

Graphvizグラフを作成します。ポートは現在画像で尊重されていませんが、各ボックスのポートインデックスを表示して明確にすることができます。

# 引数

  * `graph_name="G"`: Graphvizグラフの名前
  * `prog="neato"`: Graphvizプログラム、通常は「neato」または「fdp」
  * `box_labels=false`: ボックスに番号を付けるかどうか
  * `port_labels=false`: ポートに番号を付けるかどうか
  * `graph_attrs=Dict()`: トップレベルのグラフ属性
  * `node_attrs=Dict()`: トップレベルのノード属性
  * `edge_attrs=Dict()`: トップレベルのエッジ属性

TODO: ポートの欠如は、各ポートごとに追加のノードを導入し、そのボックスに長さ0のエッジで接続することで解決できるかもしれません。
