```
streamplot(f::function, xinterval, yinterval; color = norm, kwargs...)
```

fは`f(::Point)`または`f(x::Number, y::Number)`を受け入れる必要があります。fはPoint2を返さなければなりません。

例:

```julia
v(x::Point2{T}) where T = Point2f(x[2], 4*x[1])
streamplot(v, -2..2, -2..2)
```

## 実装

実装の詳細については、`Makie.streamplot_impl`関数を参照してください。

## プロットタイプ

`streamplot`関数のプロットタイプエイリアスは`StreamPlot`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファは掛け算されます。

**`arrow_head`** =  `automatic`  — *ドキュメントはありません。*

**`arrow_size`** =  `automatic`  — *ドキュメントはありません。*

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`平面のベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトではクリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`color`** =  `norm`  — 線の色を選択するには、`color`属性に関数`color_func(dx::Point)`を渡すことができます。これは任意の関数または関数の合成に設定できます。`color_func`に渡される`dx`は、色付けされる点での`f`の出力です。

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`および`Makie.Symlog10`の`Colorbar`と一緒にうまく機能します。

**`density`** =  `1.0`  — *ドキュメントはありません。*

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深さ値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1`。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakieのみ）。

**`gridsize`** =  `(32, 32, 32)`  — *ドキュメントはありません。*

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`によって表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`joinstyle`** =  `@inherit joinstyle`  — *ドキュメントはありません。*

**`linecap`** =  `@inherit linecap`  — *ドキュメントはありません。*

**`linestyle`** =  `nothing`  — *ドキュメントはありません。*

**`linewidth`** =  `@inherit linewidth`  — *ドキュメントはありません。*

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`maxsteps`** =  `500`  — *ドキュメントはありません。*

**`miter_limit`** =  `@inherit miter_limit`  — *ドキュメントはありません。*

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは`translate!`、`rotate!`および`scale!`で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深さチェックを無視することを意味します。

**`quality`** =  `16`  — *ドキュメントはありません。*

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`のときにのみ適用されます。

**`stepsize`** =  `0.01`  — *ドキュメントはありません。*

**`transformation`** =  `:automatic`  — *ドキュメントはありません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序に依存しない透明性を使用します。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
