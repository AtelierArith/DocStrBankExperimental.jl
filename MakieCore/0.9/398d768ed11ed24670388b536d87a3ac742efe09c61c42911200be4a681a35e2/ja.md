```
poly(vertices, indices; kwargs...)
poly(points; kwargs...)
poly(shape; kwargs...)
poly(mesh; kwargs...)
```

与えられた引数に基づいてポリゴンをプロットします。頂点とインデックスが与えられた場合、`mesh`と同様に機能します。ポイントが与えられた場合、すべてのポイントを順番に接続する1つのポリゴンを描画します。形状が与えられた場合（本質的に`GeometryBasics`によって分解可能なもの）、`decompose(shape)`をプロットします。

```
poly(coordinates, connectivity; kwargs...)
```

ポリゴンをプロットします。ポリゴンは`coordinates`（頂点の座標）と`connectivity`（頂点間のエッジ）によって定義されます。

## プロットタイプ

`poly`関数のプロットタイプエイリアスは`Poly`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファがある場合、掛け算されます。

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`平面のベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`color`** =  `@inherit patchcolor`  — ポリの色を設定します。頂点ごとの色のための`Vector{<:Colorant}`または単一の`Colorant`であることができます。テクスチャを使用してメッシュに色を付けるために`Matrix{<:Colorant}`を使用することができ、これにはメッシュがテクスチャ座標を含む必要があります。数値のベクトルまたは行列も使用でき、これによりカラーマップ引数を使用して数値を色にマッピングします。また、ポリを通常のパターンで覆うために`<: AbstractPattern`を使用することもできます。例えば、ハッチング用です。

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar`と一緒に`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`、および`Makie.Symlog10`と一緒にうまく機能します。

**`cycle`** =  `[:color => :patchcolor]`  — *ドキュメントは利用できません。*

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1`です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス、GLMakieのみ）でレンダリングされるかどうかを調整します。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`によって表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`joinstyle`** =  `@inherit joinstyle`  — *ドキュメントは利用できません。*

**`linecap`** =  `@inherit linecap`  — *ドキュメントは利用できません。*

**`linestyle`** =  `nothing`  — 線のダッシュパターンを設定します。オプションは`:solid`（`nothing`に相当）、`:dot`、`:dash`、`:dashdot`、および`:dashdotdot`です。これらはギャップスタイル修飾子とともにタプルで指定することもできます。修飾子は`:normal`、`:dense`、または`:loose`です。例えば、`(:dot, :loose)`または`(:dashdot, :dense)`のように。

カスタムパターンについては、[`Makie.Linestyle`](@ref)を参照してください。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`miter_limit`** =  `@inherit miter_limit`  — *ドキュメントは利用できません。*

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは`translate!`、`rotate!`、および`scale!`で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`shading`** =  `NoShading`  — *ドキュメントは利用できません。*

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`のときにのみ適用されます。

**`stroke_depth_shift`** =  `-1.0e-5`  — ストロークプロットの深度シフト。これはストロークとフィルの間のzファイティングを避けるのに役立ちます。

**`strokecolor`** =  `@inherit patchstrokecolor`  — マーカーの周りのアウトラインの色を設定します。

**`strokecolormap`** =  `@inherit colormap`  — 数値`color`のためにサンプリングされるカラーマップを設定します。

**`strokewidth`** =  `@inherit patchstrokewidth`  — アウトラインの幅を設定します。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序独立透明性を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
