```
GraphDisplayConfig
```

グラフ表示の設定。

## キーワード引数

  * `locs` は頂点の位置を指定するタプルのベクターです。
  * `edges` はエッジを指定するタプルのベクターです。
  * `fontsize::Float64 = 12.0`、フォントサイズ
  * `fontface::String = ""`、フォントフェイス、システムに従うには空のままにします
  * `vertex_text_color = "black"`、デフォルトのテキストカラー
  * `vertex_stroke_color = "black"`、頂点のデフォルトのストロークカラー
  * `vertex_color = "transparent"`、頂点のデフォルトの塗りつぶしカラー
  * `vertex_size::Float64 = 10.0`、デフォルトの頂点サイズ
  * `vertex_shape::Symbol = :circle`、デフォルトの頂点形状、:circle、:box、または:dotのいずれか
  * `vertex_line_width::Float64 = 1`、デフォルトの頂点ストロークの線幅
  * `vertex_line_style::String = "solid"`、頂点ストロークの線スタイル、["solid", "dotted", "dot", "dotdashed", "longdashed", "shortdashed", "dash", "dashed", "dotdotdashed", "dotdotdotdashed"]のいずれか
  * `edge_color = "black"`、デフォルトのエッジカラー
  * `edge_line_width::Float64 = 1`、デフォルトの線幅
  * `edge_style::String = "solid"`、エッジの線スタイル、["solid", "dotted", "dot", "dotdashed", "longdashed", "shortdashed", "dash", "dashed", "dotdotdashed", "dotdotdotdashed"]のいずれか
