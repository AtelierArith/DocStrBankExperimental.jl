Graphvizを使用して配線図を描画します。

入力はモルフィズム式でも構いません。その場合、最初に配線図に変換されます。この関数はGraphviz v2.42以上が必要です。

# 引数

  * `graph_name="G"`: Graphvizの有向グラフの名前
  * `orientation=TopToBottom`: レイアウトの向き。`LeftToRight`、`RightToLeft`、`TopToBottom`、または`BottomToTop`のいずれか。
  * `node_labels=true`: ノードにラベルを付けるかどうか
  * `labels=false`: エッジにラベルを付けるかどうか
  * `label_attr=:label`: エッジラベルに使用するラベルの種類（`labels`がtrueの場合）。`:label`、`:xlabel`、`:headlabel`、または`:taillabel`のいずれか。
  * `port_size="24"`: ボックスのポートの最小サイズ（ポイント単位）
  * `junction_size="0.05"`: ジャンクションノードのサイズ（インチ単位）
  * `outer_ports=true`: 外部ボックスの入力および出力ポートを表示するかどうか。無効にすると、入出力のワイヤも表示されません！
  * `anchor_outer_ports=true`: 外部ボックスの入力と出力の順序を強制するかどうか、すなわち、入出力ワイヤの順序
  * `title::Union{Nothing, Graphviz.Label}=nothing`: 図のタイトル
  * `graph_attrs=Dict()`: トップレベルのグラフ属性
  * `node_attrs=Dict()`: トップレベルのノード属性
  * `edge_attrs=Dict()`: トップレベルのエッジ属性
  * `cell_attrs=Dict()`: ノードのHTMLライクなラベル内の主要なセル属性
