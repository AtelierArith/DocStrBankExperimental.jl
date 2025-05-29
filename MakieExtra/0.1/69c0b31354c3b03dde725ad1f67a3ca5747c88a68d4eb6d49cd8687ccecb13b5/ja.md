```
scalebar(scale; kwargs...)
```

プロットにスケールバーを追加します。

すべての `lines()` および `text()` 属性をサポートし、それらをそれぞれのプロット呼び出しに転送します。`position` 属性は、スケールバーの位置を相対的な `Axis` 座標で定義します。`target_ax_frac` 属性は、スケールバーが占めるべき軸幅の割合を定義します。`scale` の倍数は自動的に選択され、スケールバーの長さが `target_ax_frac` に最も近くなるようにします。

通常、`scale` はプロット単位のサイズを定義する `Unitful` 量です。たとえば、`scalebar!(1u"mm")` はプロット単位がミリメートルであることを意味します。あるいは、`scale` は `(number, function)` のタプルであり、`function` は文字列表現のために呼び出されます。

## プロットタイプ

`scalebar` 関数のプロットタイプエイリアスは `Scalebar` です。

## 属性

**`align`** =  `(:left, :bottom)`  — `position` に対する文字列の整列を設定します。`:left, :center, :right, :top, :bottom, :baseline` または分数を使用します。

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)` のように、複数のアルファは掛け算されます。

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの `Plane3f` プレーンのベクターを設定でき、その後ろのプロットはクリップされます（つまり、見えなくなります）。デフォルトでは、クリッププレーンは親プロットまたはシーンから継承されます。`Plane3f[]` を渡すことで親の `clip_planes` を削除できます。

**`color`** =  `:black`  — *ドキュメントは利用できません。*

**`colormap`** =  `@inherit colormap :viridis`  — 数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap` の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — カラー変換関数。任意の関数を指定できますが、`Colorbar` と一緒に使用する場合は `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` の場合にのみうまく機能します。

**`cycle`** =  `nothing`  — 複数のプロットを作成する際にサイクルする属性を設定します。

**`depth_shift`** =  `0.0`  — すべての他の変換後のプロットの深度値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1` の範囲です。これは GLMakie および WGLMakie のみに適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。

**`font`** =  `@inherit font`  — フォントを設定します。`Symbol` で指定されたフォントを `fonts` 辞書で検索するか、フォントの（部分的な）名前またはフォントファイルのファイルパスを指定する `String` で指定できます。

**`fonts`** =  `@inherit fonts`  — `Symbol` で指定されたフォントを検索するための辞書として使用されます。たとえば、`:regular`、`:bold` または `:italic` などです。

**`fontsize`** =  `@inherit fontsize`  — `markerspace` に依存する単位でのフォントサイズ。

**`fxaa`** =  `false`  — プロットが fxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakie のみ）。

**`glowcolor`** =  `(:black, 0.0)`  — テキストの周りのグロー効果の色を設定します。

**`glowwidth`** =  `0.0`  — テキストの周りのグロー効果のサイズを設定します。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector でカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspector によって生成されるデフォルトのラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`joinstyle`** =  `@inherit joinstyle`  — コーナーでのレンダリングを制御します。オプションは、鋭いコーナーのための `:miter`、"切り取られた" コーナーのための `:bevel`、丸みを帯びたコーナーのための `:round` です。コーナー角度が `miter_limit` 未満の場合、`:miter` は長いスパイクを避けるために `:bevel` と同等です。

**`justification`** =  `automatic`  — テキストの境界ボックスに対する整列を設定します。`:left, :center, :right` または分数を指定できます。デフォルトは `align` の水平方向の整列になります。

**`linecap`** =  `@inherit linecap`  — 使用されるラインキャップのタイプを設定します。オプションは、`:butt`（押し出しなしの平坦）、`:square`（半分のライン幅の押し出し付きの平坦）、または `:round` です。

**`lineheight`** =  `1.0`  — 行の高さの倍率。

**`linestyle`** =  `nothing`  — 線のダッシュパターンを設定します。オプションは `:solid`（`nothing` と同等）、`:dot`、`:dash`、`:dashdot` および `:dashdotdot` です。これらは、ギャップスタイル修飾子 `:normal`、`:dense` または `:loose` を持つタプルでも指定できます。たとえば、`(:dot, :loose)` または `(:dashdot, :dense)` です。

カスタムパターンについては [`Makie.Linestyle`](@ref) を参照してください。

**`linewidth`** =  `@inherit linewidth`  — スクリーン単位での線の幅を設定します。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`markerspace`** =  `:pixel`  — `fontsize` が作用する空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`miter_limit`** =  `@inherit miter_limit`  — ミタージョインが切り取られる最小内側ジョイン角度を設定します。`Makie.miter_distance_to_angle` も参照してください。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行われた調整を上書きします。

**`muls`** =  `[if p isa Int     x * p else     round(x * p, sigdigits = 4) end for p = Real[[10.0 ^ p for p = -50:-1]; [1, 10, 100, 1000, 10000]; [10.0 ^ p for p = 5:50]] for x = [1, 2, 5]]`  — *ドキュメントは利用できません。*

**`nan_color`** =  `:transparent`  — NaN 値の色。

**`offset`** =  `(0.0, 0.0)`  — `markerspace` 単位での指定位置からのテキストのオフセット。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特に GL バックエンドで深度チェックを無視することを意味します。

**`position`** =  `Point2(0.85, 0.08)`  — *ドキュメントは利用できません。*

**`rotation`** =  `0.0`  — 指定位置の周りでテキストを回転させます。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`ssao`** =  `false`  — プロットが ssao（スクリーンスペース環境遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`strokecolor`** =  `(:black, 0.0)`  — マーカーの周りのアウトラインの色を設定します。

**`strokewidth`** =  `0`  — マーカーの周りのアウトラインの幅を設定します。

**`target_ax_frac`** =  `0.2`  — *ドキュメントは利用できません。*

**`text`** =  `""`  — 表示するテキストの一部またはテキストのベクターを指定します。数は指定された位置の数と一致する必要があります。Makie は通常のテキストに使用される `String` と、`MathTeXEngine.jl` を使用して数式をレイアウトする `LaTeXString` をサポートしています。

**`transform_marker`** =  `false`  — モデル行列（平行移動なし）がグリフ自体に適用されるかどうかを制御します。これが真の場合、`scale!` および `rotate!` はテキストグリフに影響を与えます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakie では `transparency = true` は順序に依存しない透明性を使用します。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。

**`word_wrap_width`** =  `-1`  — テキストのライン幅制限を指定します。この制限を超える単語がある場合、その前に改行が挿入されます。負の数は単語の折り返しを無効にします。
