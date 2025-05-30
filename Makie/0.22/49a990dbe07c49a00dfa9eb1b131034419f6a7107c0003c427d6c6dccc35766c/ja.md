```
textlabel(positions, text; attributes...)
textlabel(position; text, attributes...)
textlabel(text_position; attributes...)
```

指定された位置に背景を持つテキストを描画します。

## プロットタイプ

`textlabel`関数のプロットタイプエイリアスは`TextLabel`です。

## 属性

**`alpha`** =  `1.0`  — 背景のアルファ値（不透明度）を設定します。

**`background_color`** =  `:white`  — 背景の色を設定します。頂点ごとの色のために`Vector{<:Colorant}`、単一の`Colorant`、またはハッチング用の通常のパターンでポリを覆う`<: AbstractPattern`を指定できます。

**`clip_planes`** =  `Plane3f[]`  — クリップ平面は3D空間でのクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`平面のベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`cornerradius`** =  `5.0`  — Rect2背景形状が与えられたときのコーナー半径を設定します。

**`cornervertices`** =  `10`  — 丸みを帯びたコーナーに関与する頂点の数を設定します。少なくとも2でなければなりません。

**`depth_shift`** =  `0.0`  — 他のすべての変換の後にテキストラベルの深度値を調整します。すなわち、クリップ空間で`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`draw_on_top`** =  `true`  — テキストラベルが前面に描画されるか（true、デフォルト）、その位置に適した深度で描画されるかを制御します。

**`font`** =  `@inherit font`  — フォントを設定します。`fonts`辞書で検索される`Symbol`、またはフォントの（部分的な）名前やフォントファイルのファイルパスを指定する`String`を指定できます。

**`fonts`** =  `@inherit fonts`  — `Symbol`で指定されたフォントを検索するための辞書として使用されます。例えば、`:regular`、`:bold`、または`:italic`などです。

**`fontsize`** =  `@inherit fontsize`  — ピクセル単位のフォントサイズです。

**`fxaa`** =  `false`  — 背景がfxaa（アンチエイリアス、GLMakieのみ）でレンダリングされるかどうかを制御します。これはデフォルトで`false`に設定されており、テキストの周りのアーティファクトを防ぎます。

**`inspectable`** =  `@inherit inspectable`  — プロットがssao（スクリーンスペース環境遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`のときにのみ適用されます。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`joinstyle`** =  `@inherit joinstyle`  — アウトラインコーナーのレンダリングを制御します。オプションは、鋭いコーナーのための`:miter`、"切り取られた"コーナーのための`:bevel`、および丸みを帯びたコーナーのための`:round`です。コーナー角度が`miter_limit`未満の場合、`:miter`は長いスパイクを避けるために`:bevel`と同等です。

**`justification`** =  `automatic`  — テキストの境界ボックスに対する整列を設定します。`:left, :center, :right`または分数を指定できます。デフォルトでは`text_align`の水平方向の整列になります。

**`keep_aspect`** =  `false`  — リスケーリング中に背景形状のアスペクト比が保持されるかどうかを制御します。

**`lineheight`** =  `1.0`  — 行の高さの倍率です。

**`linestyle`** =  `nothing`  — アウトラインのダッシュパターンを設定します。オプションは、`:solid`（`nothing`と同等）、`:dot`、`:dash`、`:dashdot`、および`:dashdotdot`です。これらは、ギャップスタイル修飾子`(:normal, :dense, :loose)`を持つタプルでも指定できます。例えば、`(:dot, :loose)`や`(:dashdot, :dense)`などです。

カスタムパターンについては、[`Makie.Linestyle`](@ref)を参照してください。

**`miter_limit`** =  `@inherit miter_limit`  — ミタージョインが切り捨てられる最小内側ジョイン角度を設定します。`Makie.miter_distance_to_angle`も参照してください。

**`offset`** =  `(0.0, 0.0)`  — 指定された位置からのテキストラベルのオフセットを`markerspace`単位で設定します。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`padding`** =  `4`  — テキストの境界ボックスと背景形状の間のパディングを設定します。

**`position`** =  `(0, 0)`  — 非推奨：テキストの位置を指定します。代わりに`text`への位置引数を使用してください。

**`shading`** =  `NoShading`  — 背景が光に反応するかどうかを制御します。

**`shape`** =  `Rect2f(0, 0, 1, 1)`  — 背景の形状を制御します。GeometryPrimitive、メッシュ、または関数`(origin, size) -> coordinates`を指定できます。前者の2つのオプションは、レンダリングされたテキストのパディングされた境界ボックスに自動的にリスケーリングされます。デフォルトでは、(0, 0)がパディングされた境界ボックスの左下隅、(1, 1)が右上隅になります。`shape_limits`を参照してください。

**`shape_limits`** =  `Rect2f(0, 0, 1, 1)`  — テキストの境界ボックスのサイズに一致するように変換される`shape`空間の座標を設定します。例えば、`shape_limits = Rect2f(-1, -1, 2, 2)`は、(-1, 1)をパディングされたテキストの境界ボックスの左下隅に、(1, 1)を右上隅に変換します。`shape`がこの範囲の外に座標を含む場合、それらはパディングされたテキストの境界ボックスの外に描画されます。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`stroke_alpha`** =  `1.0`  — 背景アウトラインのアルファ値（不透明度）を設定します。

**`strokecolor`** =  `:black`  — 背景の周りのアウトラインの色を設定します。

**`strokewidth`** =  `1`  — アウトラインの幅を設定します。

**`text`** =  `""`  — 表示するテキストの1つの部分またはテキストのベクトルを指定します。数は指定された位置の数と一致する必要があります。Makieは、通常のテキストに使用される`String`と、`MathTeXEngine.jl`を使用して数式をレイアウトする`LaTeXString`をサポートしています。

**`text_align`** =  `(:center, :center)`  — `position`に対する文字列の整列を設定します。`:left, :center, :right, :top, :bottom, :baseline`または分数を使用します。

**`text_alpha`** =  `1.0`  — テキストのアルファ値（不透明度）を設定します。

**`text_color`** =  `@inherit textcolor`  — テキストの色を設定します。`Vector{<:Colorant}`を渡すことで、各グリフごとに1色を設定するか、全体のテキストに1つの色を設定できます。

**`text_fxaa`** =  `false`  — テキストがfxaa（アンチエイリアス、GLMakieのみ）でレンダリングされるかどうかを制御します。これをtrueに設定すると、テキストの品質が低下します。

**`text_glowcolor`** =  `(:black, 0.0)`  — テキストの周りのグロー効果の色を設定します。

**`text_glowwidth`** =  `0.0`  — テキストの周りのグロー効果のサイズを設定します。

**`text_rotation`** =  `0.0`  — 指定された位置の周りでテキストを回転させます。これはテキストラベルのサイズに影響しますが、その回転には影響しません。

**`text_strokecolor`** =  `(:black, 0.0)`  — テキストの周りのアウトラインの色を設定します。

**`text_strokewidth`** =  `0`  — テキストの周りのアウトラインの幅を設定します。

**`transparency`** =  `false`  — プロットが透明度をどのように扱うかを調整します。GLMakieでは、`transparency = true`は順序に依存しない透明度を使用します。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。

**`word_wrap_width`** =  `-1`  — テキストの行幅制限を指定します。この制限を超える単語がある場合、その前に改行が挿入されます。負の数は単語の折り返しを無効にします。
