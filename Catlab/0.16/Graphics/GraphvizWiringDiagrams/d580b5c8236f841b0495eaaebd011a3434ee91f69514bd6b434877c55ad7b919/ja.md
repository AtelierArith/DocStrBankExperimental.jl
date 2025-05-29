Graphvizを使用して無向配線図を描画します。

無向の二部グラフであるGraphvizグラフを作成し、図のボックスと外部ポートが一方の種類のノードになり、図の接続点がもう一方の種類のノードになります。

# 引数

  * `graph_name="G"`: Graphvizグラフの名前
  * `prog="neato"`: Graphvizプログラム、通常は「neato」または「fdp」
  * `box_labels=false`: ブール値の場合、ボックスに番号を付けるかどうか; シンボルの場合、ボックスラベルのデータ属性の名前
  * `port_labels=false`: ポートに番号を付けるかどうか
  * `junction_labels=false`: ブール値の場合、接続点に番号を付けるかどうか; シンボルの場合、接続点ラベルのデータ属性の名前
  * `junction_size="0.075"`: 接続点ノードのサイズ（インチ）
  * `implicit_junctions=false`: ちょうど2つの接続ポートがある場合、接続点をワイヤーとして暗黙的に表現するかどうか
  * `title::Union{Nothing, Graphviz.Label}=nothing`: 図のタイトル
  * `graph_attrs=Dict()`: トップレベルのグラフ属性
  * `node_attrs=Dict()`: トップレベルのノード属性
  * `edge_attrs=Dict()`: トップレベルのエッジ属性
