```
contour3d(x, y, z)
```

x::Vector、y::Vector、z::Matrixをスパンする平面の3D等高線プロットを作成し、各レベルのz-標高を表示します。

## プロットタイプ

`contour3d`関数のプロットタイプエイリアスは`Contour3d`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファがある場合、掛け算されます。

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`プレーンのベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリッププレーンは親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`color`** =  `nothing`  — 等高線の色。`nothing`の場合、色は等高線レベルの数値と`colormap`および`colorrange`の組み合わせによって決まります。

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar`と一緒に使用する場合は`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`および`Makie.Symlog10`と一緒にうまく機能します。

**`depth_shift`** =  `0.0`  — すべての他の変換後のプロットの深度値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`enable_depth`** =  `true`  — *ドキュメントは利用できません。*

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakieのみ）。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`で表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`joinstyle`** =  `@inherit joinstyle`  — *ドキュメントは利用できません。*

**`labelcolor`** =  `nothing`  — 等高線ラベルの色。`nothing`の場合、デフォルトで`color`に一致します。

**`labelfont`** =  `@inherit font`  — 等高線ラベルのフォント。

**`labelformatter`** =  `contour_label_formatter`  — 等高線レベルの数値を文字列にフォーマットします。

**`labels`** =  `false`  — `true`の場合、等高線にテキストラベルを追加します。

**`labelsize`** =  `10`  — 等高線ラベルのフォントサイズ。

**`levels`** =  `5`  — 等高線の数と位置を制御します。次のいずれかです。

  * n等幅のレベルまたはバンドを生成する`Int`
  * 低から高までのn連続エッジをリストする`AbstractVector{<:Real}`で、n-1のレベルまたはバンドを生成します。

**`linecap`** =  `@inherit linecap`  — *ドキュメントは利用できません。*

**`linestyle`** =  `nothing`  — *ドキュメントは利用できません。*

**`linewidth`** =  `1.0`  — *ドキュメントは利用できません。*

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`miter_limit`** =  `@inherit miter_limit`  — *ドキュメントは利用できません。*

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは`translate!`、`rotate!`および`scale!`で行った調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境光遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`のときにのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明度をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序独立透明度を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
