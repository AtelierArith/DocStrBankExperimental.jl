```
text(positions; text, kwargs...)
text(x, y; text, kwargs...)
text(x, y, z; text, kwargs...)
```

`text`キーワードを介して渡された1つまたは複数のテキストをプロットします。`Text`は`PointBased`変換トレイトを使用します。

## プロットタイプ

`text`関数のプロットタイプエイリアスは`Text`です。

## 属性

**`align`** =  `(:left, :bottom)`  — 文字列の位置に対する整列を設定します。`:left, :center, :right, :top, :bottom, :baseline`または分数を使用します。

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファは掛け算されます。

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`平面のベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`color`** =  `@inherit textcolor`  — テキストの色を設定します。`Vector{<:Colorant}`を渡すことで、各グリフごとに1つの色を設定するか、全体のテキストに1つの色を設定できます。色が数のベクトルの場合、カラーマップ引数が数を色にマッピングするために使用されます。

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar`と一緒に使用する場合は`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`および`Makie.Symlog10`と一緒にうまく機能します。

**`depth_shift`** =  `0.0`  — すべての他の変換後のプロットの深度値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`font`** =  `@inherit font`  — フォントを設定します。`fonts`辞書で検索される`Symbol`、またはフォントの（部分的な）名前やフォントファイルのファイルパスを指定する`String`にすることができます。

**`fonts`** =  `@inherit fonts`  — `Symbol`で指定されたフォントを検索するための辞書として使用されます。例えば、`:regular`、`:bold`または`:italic`などです。

**`fontsize`** =  `@inherit fontsize`  — `markerspace`に依存する単位でのフォントサイズ。

**`fxaa`** =  `false`  — プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakieのみ）。

**`glowcolor`** =  `(:black, 0.0)`  — テキストの周りのグロー効果の色を設定します。

**`glowwidth`** =  `0.0`  — テキストの周りのグロー効果のサイズを設定します。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`によって表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`justification`** =  `automatic`  — テキストのバウンディングボックスに対する整列を設定します。`:left, :center, :right`または分数にすることができます。デフォルトは`align`の水平方向の整列になります。

**`lineheight`** =  `1.0`  — 行の高さの倍率。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`markerspace`** =  `:pixel`  — `fontsize`が作用する空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは`translate!`、`rotate!`および`scale!`で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN値の色。

**`offset`** =  `(0.0, 0.0)`  — `markerspace`単位で指定された位置からのテキストのオフセット。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`position`** =  `(0.0, 0.0)`  — 非推奨：テキストの位置を指定します。代わりに`text`への位置引数を使用してください。

**`rotation`** =  `0.0`  — 指定された位置の周りでテキストを回転させます。

**`space`** =  `:data`  — プロットを囲むボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境光遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`のときにのみ適用されます。

**`strokecolor`** =  `(:black, 0.0)`  — マーカーの周りのアウトラインの色を設定します。

**`strokewidth`** =  `0`  — マーカーの周りのアウトラインの幅を設定します。

**`text`** =  `""`  — 表示するテキストの1つの部分またはテキストのベクトルを指定します。数は与えられた位置の数と一致する必要があります。Makieは通常のテキストに使用される`String`と、`MathTeXEngine.jl`を使用して数式をレイアウトする`LaTeXString`をサポートしています。

**`transform_marker`** =  `false`  — モデル行列（平行移動なし）がグリフ自体に適用されるかどうかを制御します。これが真の場合、`scale!`および`rotate!`はテキストグリフに影響を与えます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序に依存しない透明性を使用します。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。

**`word_wrap_width`** =  `-1`  — テキストの行幅制限を指定します。この制限を超える単語がある場合、その前に改行が挿入されます。負の数は単語の折り返しを無効にします。
