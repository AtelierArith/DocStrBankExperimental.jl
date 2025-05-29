```
img_maskedgrid(maskedgrid::MaskedGrid;
    colors=[DEFAULT_LINE_COLOR[], ...],
    texts=["1", "2", ...],
    vectors=[],
    format=:svg,
    filename=nothing,
    kwargs...
    )
```

`colors`で指定された色と`texts`で指定されたテキストを使用して`maskedgrid`を描画します。画像を表示するには、`VSCode`、`Pluto`ノートブック、または`Jupyter`ノートブックが必要です。

### キーワード引数

##### features

  * `colors`はノードの色のベクトルです
  * `texts`はノードに表示される文字列のベクトルです
  * `vectors`は矢印のリストを指定するための(start*loc, end*loc)ペアのベクトルです。

##### IO

  * `format`は`:svg`、`:pdf`、または`:png`を指定できます
  * `filename`は`.svg`、`.png`、または`.pdf`のサフィックスを持つファイル名文字列です

##### general

  * `background_color = DEFAULT_BACKGROUND_COLOR[]`
  * `scale::Int = 60.0`は単位長さあたりのピクセル数です
  * `xpad::Float64 = 2.5`はx軸のパディングスペースです
  * `ypad::Float64 = 1.5`はy軸のパディングスペースです

##### axes

  * `axes_text_color = DEFAULT_TEXT_COLOR[]`
  * `axes_text_fontsize::Float64 = 16.0`
  * `axes_num_of_xticks = 5`
  * `axes_num_of_yticks = 5`
  * `axes_x_offset::Float64 = 0.5`
  * `axes_y_offset::Float64 = 0.5`
  * `axes_unit::String = "μm"`

##### node

  * `node_text_fontsize::Float64 = 16.0`
  * `node_text_color = DEFAULT_TEXT_COLOR[]`
  * `node_stroke_color = DEFAULT_LINE_COLOR[]`
  * `node_stroke_linewidth = 1`
  * `node_fill_color = DEFAULT_NODE_COLOR[]`

##### bond

  * `bond_color = DEFAULT_LINE_COLOR[]`
  * `bond_linewidth::Float64 = 1.0`

##### blockade

  * `blockade_radius::Float64=0`、`blockade_radius`内の原子はエッジで接続されます。
  * `blockade_style::String = "none"`、"none"または"dashed"を指定できます
  * `blockade_stroke_color = DEFAULT_LINE_COLOR[]`
  * `blockade_fill_color = "transparent"`
  * `blockade_fill_opacity::Float64 = 0.5`
  * `blockade_stroke_linewidth = 1.0`   # pt単位

##### arrow

  * `arrow_linewidth`
  * `arrow_color`
  * `arrow_head_length`

##### grid

  * `grid_stroke_color="#AAAAAA"`
  * `grid_stroke_width::Float64=1`
  * `grid_stroke_style::String="dashed"`
