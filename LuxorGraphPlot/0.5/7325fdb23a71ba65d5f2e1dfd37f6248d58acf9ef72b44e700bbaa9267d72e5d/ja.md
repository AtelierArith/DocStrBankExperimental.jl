```
show_graph([f, ]graph::AbstractGraph;
    kwargs...
    )
```

VSCode、Pluto、またはJupyterノートブックでグラフを表示するか、ファイルに保存します。

## 位置引数

  * `f` は追加の `Luxor` プロットステートメントを返す関数です。
  * `graph` はグラフインスタンスです。
  * `locs` は頂点の位置を指定するためのタプルのベクター、または [`AbstractLayout`](@ref) インスタンスです。

## キーワード引数

  * `config` は [`GraphDisplayConfig`](@ref) インスタンスです。
  * `vertex_colors` は頂点の塗りつぶし色を指定するための色文字列のベクターです。
  * `vertex_sizes` は頂点のサイズを指定するための実数のベクターです。
  * `vertex_shapes` は頂点の形状を指定するための文字列のベクターで、文字列は "circle" または "box" である必要があります。
  * `vertex_stroke_colors` は頂点のストローク色を指定するための色文字列のベクターです。
  * `vertex_text_colors` は頂点のテキスト色を指定するための色文字列のベクターです。
  * `edge_colors` はエッジの色を指定するための色文字列のベクターです。
  * `texts` は頂点にラベルを付けるための文字列のベクターです。
  * `padding_left::Int = 10`、描画の左側のパディング
  * `padding_right::Int = 10`、描画の右側のパディング
  * `padding_top::Int = 10`、描画の上側のパディング
  * `padding_bottom::Int = 10`、描画の下側のパディング
  * `format` は出力形式で、`:svg`、`:png` または `:pdf` です。
  * `filename` は出力ファイル名としての文字列です。

## 例

```jldoctest
julia> using Graphs, LuxorGraphPlot

julia> show_graph(smallgraph(:petersen); format=:png, vertex_colors=rand(["blue", "red"], 10));
```
