```
graphplot(graph::AbstractGraph)
graphplot!(ax, graph::AbstractGraph)
```

ネットワーク `graph` のプロットを作成します。複数のステップで構成されています：

  * ノードのレイアウト：`layout` 属性を参照してください。ノードの位置は、プロットオブジェクト `p` の外部から `p[:node_pos]` を使用して観測可能です。
  * エッジを `edgeplot` プロットとして描画
  * `arrow_show` が真の場合、矢印の先端を `scatter` プロットとして描画
  * ノードを `scatter` プロットとして描画
  * `nlabels!=nothing` の場合、ノードラベルを `text` プロットとして描画
  * `elabels!=nothing` の場合、エッジラベルを `text` プロットとして描画

サブプロットの主な属性は `graphplot` の属性として公開されています。`scatter`、`edgeplot` および `text` プロットの追加属性は、`node_attr`、`edge_attr`、`nlabels_attr` および `elabels_attr` に名前付きタプルとして提供できます。

ほとんどの引数は、エッジ/ノードの長さのベクトルとして、または単一の値として与えることができます。基盤となるグラフを変更し、エッジ/ノードの数を変更するとエラーが発生する可能性があります。

## 属性

### 主な属性

  * `layout=Spring()`: 基本レイアウトを決定する関数 `AbstractGraph->Vector{Point}` または `Vector{Point}`。`Spring`、`Stress`、`Spectral` など、[NetworkLayout.jl](https://https://github.com/JuliaGraphs/NetworkLayout.jl) の任意のネットワークレイアウトも使用できます。
  * `node_color=automatic`: `ilabels` がない場合、デフォルトは `scatter_theme.color` です。
  * `node_size=automatic`: `ilabels` がない場合、デフォルトは `scatter_theme.markersize` です。それ以外の場合、`ilabels` のサイズに基づいてノードサイズを選択します。
  * `node_marker=automatic`: `ilabels` がない場合、デフォルトは `scatter_theme.marker` です。
  * `node_strokewidth=automatic` デフォルトは `scatter_theme.strokewidth` です。`ilabels` がない場合。
  * `node_attr=(;)`: `scatter` コマンドに渡される kw 引数のリスト
  * `edge_color=lineseg_theme.color`: エッジの色。
  * `edge_width=lineseg_theme.linewidth`: エッジごとに2つの幅を持つベクトルを渡して、尖ったエッジを取得します。
  * `edge_attr=(;)`: `linesegments` コマンドに渡される kw 引数のリスト
  * `arrow_show=Makie.automatic`: `Bool`、矢印の先端でエッジの方向を示しますか？ デフォルトは `Graphs.is_directed(graph)` です。
  * `arrow_marker='➤'`
  * `arrow_size=scatter_theme.markersize`: 矢印のサイズ。
  * `arrow_shift=0.5`: ソース (0) から宛先 (1) ノードへの矢印位置をシフトします。 `arrow_shift=:end` の場合、矢印の先端は宛先ノードの表面に配置されます（宛先ノードが円形であると仮定）。
  * `arrow_attr=(;)`: `scatter` コマンドに渡される kw 引数のリスト

### ノードラベル

各ラベルの位置は、ノードの位置にデータ空間でのオフセットを加えたものによって決まります。

  * `nlabels=nothing`: 各ノードのラベルを持つ `Vector{String}`
  * `nlabels_align=(:left, :bottom)`: テキストフィールドのアンカー。
  * `nlabels_distance=0.0`: アラインの方向にノードからのピクセル距離。
  * `nlabels_color=labels_theme.color`
  * `nlabels_offset=nothing`: `Point` または `Vector{Point}`（データ空間内）
  * `nlabels_fontsize=labels_theme.fontsize`
  * `nlabels_attr=(;)`: `text` コマンドに渡される kw 引数のリスト

### 内部ノードラベル

マーカーの内部にラベルを配置します。ラベルが提供されている場合、デフォルトの属性を `node_marker=Circle`、`node_strokewidth=1` および `node_color=:gray80` に変更します。`node_size` は `ilabels` のサイズに一致します。

  * `ilabels=nothing`: 各ノードのラベルを持つ `Vector`
  * `ilabels_color=labels_theme.color`
  * `ilabels_fontsize=labels_theme.fontsize`
  * `ilabels_attr=(;)`: `text` コマンドに渡される kw 引数のリスト

### エッジラベル

各ラベルの基本位置は `src + shift*(dst-src)` によって決まります。追加の `distance` パラメータはピクセル単位で、テキストをエッジから離します。

  * `elabels=nothing`: 各エッジのラベルを持つ `Vector{String}`
  * `elabels_align=(:center, :center)`: テキストフィールドのアンカー。
  * `elabels_side = :left`: エッジラベルテキストを配置するエッジの側
  * `elabels_distance=Makie.automatic`: アンカーからエッジまでのピクセル距離。方向は `elabels_side` に基づいて決定されます。
  * `elabels_shift=0.5`: エッジの src と dst の間の位置。
  * `elabels_rotation=Makie.automatic`: 各ラベルのテキストの角度。`nothing` の場合、エッジの角度によって決定されます。`automatic` の場合、上向きにポイントされ、読みやすくなります。
  * `elabels_offset=nothing`: データ空間内の追加オフセット
  * `elabels_color=labels_theme.color`
  * `elabels_fontsize=labels_theme.fontsize`
  * `elabels_attr=(;)`: `text` コマンドに渡される kw 引数のリスト

### 曲線エッジと自己エッジ/ループ

  * `edge_plottype=Makie.automatic()`: `automatic`、`:linesegments` または `:beziersegments` のいずれか。`：beziersegments` は大きなグラフでは非常に遅くなります！

自己エッジ / ループ：

  * `selfedge_size=Makie.automatic()`: 自己ループのサイズ（辞書/ベクトル可能）。
  * `selfedge_direction=Makie.automatic()`: `Point2` としての自己ループの中心の方向（辞書/ベクトル可能）。
  * `selfedge_width=Makie.automatic()`: 自己ループの開口部のラジアン（辞書/ベクトル可能）。
  * 注意：自己ループの有効なウェイポイントが提供されている場合、上記の自己エッジ属性は無視されます。

曲線エッジのための高レベルインターフェース：

  * `curve_distance=0.1`:

    （現在曲がった）線と直線の間の距離を *データ空間* で指定します。単一の値、配列、または辞書として指定できます。ユーザーが提供した `tangents` または `waypoints` がこのプロパティを上書きします。
  * `curve_distance_usage=Makie.automatic()`:

    `Makie.automatic()` の場合、曲線的に二重エッジのみをプロットします。他のオプションは `true` と `false` です。

曲線エッジのための接線インターフェース：

  * `tangents=nothing`:

    各エッジ（src と dst）の接線ベクトルのペアを指定します。`nothing`（または辞書にエッジインデックスがない場合）の場合、直線を描画します。
  * `tfactor=0.6`:

    接線からベジエウェイポイントを計算するために使用される係数。高い係数は大きな半径を意味します。src と dst に異なる係数を指定するために、エッジごとにタプルを使用できます。
  * 注意：ウェイポイントが提供されていない場合、自己ループでは接線は無視されます。

エッジに沿ったウェイポイント：

  * `waypoints=nothing`

    エッジのためのウェイポイントを指定します。このパラメータはベクトルまたは辞書として指定する必要があります。ウェイポイントは自然な三次スプラインを使用して交差します。ウェイポイントには src/dst の位置が含まれる場合と含まれない場合があります。
  * `waypoint_radius=nothing`

    属性 `waypoint_radius` が `nothing` または `:spline` の場合、ウェイポイントは自然な三次スプライン補間を使用して交差します。数値（辞書/ベクトル可能）の場合、ウェイポイントには到達せず、代わりに与えられた半径の周りで曲がる直線で接続されます。
