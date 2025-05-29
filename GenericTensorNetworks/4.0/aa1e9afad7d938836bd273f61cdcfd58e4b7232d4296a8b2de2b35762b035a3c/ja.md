```
show_einsum(ein::AbstractEinsum;
    tensor_locs=nothing,
    label_locs=nothing,  # dict
    spring::Bool=true,
    optimal_distance=25.0,

    tensor_size=15,
    tensor_color="black",
    tensor_text_color="white",
    annotate_tensors=false,

    label_size=7,
    label_color="black",
    open_label_color="black",
    annotate_labels=true,
    kwargs...
    )
```

## 位置引数

  * `ein` はEinsum収縮コードです（パッケージ `OMEinsum` によって提供されます）。

## キーワード引数

  * `locs` は `tensor_locs`（ベクトル）と `label_locs`（辞書）のタプルです。
  * `spring` は位置を最適化するためにスプリング法を使用するスイッチです。
  * `optimal_distance` は `spring` オプティマイザのための最適距離パラメータです。
  * `tensor_color` はテンソルノードの色を指定するための文字列です。
  * `tensor_size` はテンソルノードのサイズを指定するための実数です。
  * `tensor_text_color` はテンソルテキストの色を指定するための色の文字列です。
  * `annotate_tensors` は異なるテンソルを整数で注釈するためのブールスイッチです。
  * `label_size` はラベルテキストノードのサイズを指定するための実数です。
  * `label_color` はラベルテキストの色を指定するための色の文字列です。
  * `open_label_color` はオープンラベルテキストの色を指定するための色の文字列です。
  * `annotate_labels` は異なるラベルを注釈するためのブールスイッチです。
  * `format` は出力形式で、`:svg`、`:png` または `:pdf` のいずれかです。
  * `filename` は出力ファイル名としての文字列です。
  * `fontsize::Float64 = 12.0`、フォントサイズ
  * `fontface::String = ""`、フォントフェイス、空白のままにしてシステムに従う
  * `vertex_text_color = "black"`、デフォルトのテキストカラー
  * `vertex_stroke_color = "black"`、頂点のデフォルトストロークカラー
  * `vertex_color = "transparent"`、頂点のデフォルトの塗りつぶしカラー
  * `vertex_size::Float64 = 10.0`、デフォルトの頂点サイズ
  * `vertex_shape::Symbol = :circle`、デフォルトの頂点形状、:circle、:box または :dot のいずれか
  * `vertex_line_width::Float64 = 1`、デフォルトの頂点ストロークライン幅
  * `vertex_line_style::String = "solid"`、頂点ストロークのラインスタイル、["solid", "dotted", "dot", "dotdashed", "longdashed", "shortdashed", "dash", "dashed", "dotdotdashed", "dotdotdotdashed"] のいずれか
  * `edge_color = "black"`、デフォルトのエッジカラー
  * `edge_line_width::Float64 = 1`、デフォルトのライン幅
  * `edge_style::String = "solid"`、エッジのラインスタイル、["solid", "dotted", "dot", "dotdashed", "longdashed", "shortdashed", "dash", "dashed", "dotdotdashed", "dotdotdotdashed"] のいずれか
