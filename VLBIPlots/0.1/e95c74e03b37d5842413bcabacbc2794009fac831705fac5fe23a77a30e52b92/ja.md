ドキュメント文字列が定義されていません。

## プロットタイプ

`beampoly` 関数のプロットタイプエイリアスは `BeamPoly` です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファがある場合、掛け算されます。

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの `Plane3f` プレーンのベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリッププレーンは親プロットまたはシーンから継承されます。`Plane3f[]` を渡すことで親の `clip_planes` を削除できます。

**`color`** =  `@inherit patchcolor`  — ポリの色を設定します。頂点ごとの色のための `Vector{<:Colorant}` または単一の `Colorant` であることができます。テクスチャを使用してメッシュに色を付けるために `Matrix{<:Colorant}` を使用することができ、これにはメッシュがテクスチャ座標を含む必要があります。数値のベクトルまたは行列も使用でき、これにより数値が色にマッピングされるカラーマップ引数が使用されます。また、ポリを通常のパターンで覆うために `<: AbstractPattern` を使用することもできます。例えば、ハッチング用です。

**`colormap`** =  `@inherit colormap :viridis`  — 数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap` の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar` と一緒に `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` と一緒にうまく機能します。

**`cycle`** =  `[:color => :patchcolor]`  — *ドキュメントは利用できません。*

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1` の範囲です。これは GLMakie と WGLMakie のみに適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `true`  — プロットが fxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakie のみ）。

**`highclip`** =  `automatic`  — カラー範囲を超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector でカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspector によって生成されるデフォルトのラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`joinstyle`** =  `@inherit joinstyle`  — *ドキュメントは利用できません。*

**`linecap`** =  `@inherit linecap`  — *ドキュメントは利用できません。*

**`linestyle`** =  `nothing`  — 線のダッシュパターンを設定します。オプションは `:solid`（`nothing` と同等）、`:dot`、`:dash`、`:dashdot` および `:dashdotdot` です。これらはギャップスタイル修飾子とともにタプルで指定することもできます。修飾子は `:normal`、`:dense` または `:loose` です。例えば、`(:dot, :loose)` または `(:dashdot, :dense)` のように。

カスタムパターンについては [`Makie.Linestyle`](@ref) を参照してください。

**`lowclip`** =  `automatic`  — カラー範囲未満の任意の値の色。

**`miter_limit`** =  `@inherit miter_limit`  — *ドキュメントは利用できません。*

**`model`** =  `automatic`  — プロットのためのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN 値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特に GL バックエンドで深度チェックを無視することを意味します。

**`position`** =  `Point2(0.1, 0.1)`  — *ドキュメントは利用できません。*

**`shading`** =  `NoShading`  — *ドキュメントは利用できません。*

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`ssao`** =  `false`  — プロットが ssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`stroke_depth_shift`** =  `-1.0e-5`  — ストロークプロットの深度シフト。これはストロークとフィルの間の z-fighting を避けるのに役立ちます。

**`strokecolor`** =  `@inherit patchstrokecolor`  — マーカーの周りのアウトラインの色を設定します。

**`strokecolormap`** =  `@inherit colormap`  — 数値 `color` のためにサンプリングされるカラーマップを設定します。

**`strokewidth`** =  `@inherit patchstrokewidth`  — アウトラインの幅を設定します。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakie では `transparency = true` は順序独立透明性を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
