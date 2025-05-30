```
barplot(positions, heights; kwargs...)
```

棒グラフをプロットします。

## プロットタイプ

`barplot`関数のプロットタイプエイリアスは`BarPlot`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファがある場合、掛け算されます。

**`bar_labels`** =  `nothing`  — 各バーの端に追加されるラベル。

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`プレーンのベクターを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリッププレーンは親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`color`** =  `@inherit patchcolor`  — *ドキュメントは利用できません。*

**`color_over_background`** =  `automatic`  — *ドキュメントは利用できません。*

**`color_over_bar`** =  `automatic`  — *ドキュメントは利用できません。*

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを見るには、`Makie.available_gradients()`を呼び出します。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar`と一緒に`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`、`Makie.Symlog10`と一緒にうまく機能します。

**`cycle`** =  `[:color => :patchcolor]`  — *ドキュメントは利用できません。*

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieとWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`direction`** =  `:y`  — バーの方向を制御します。`:y`（垂直）または`:x`（水平）にできます。

**`dodge`** =  `automatic`  — *ドキュメントは利用できません。*

**`dodge_gap`** =  `0.03`  — *ドキュメントは利用できません。*

**`fillto`** =  `automatic`  — バーのベースラインを制御します。これはデフォルトの`automatic`の場合はゼロですが、バーグラフが対数スケールの`Axis`にある場合は異なります。対数スケールの場合、デフォルトは最小値の半分です。なぜなら、ゼロは対数スケールにとって無効な値だからです。

**`flip_labels_at`** =  `Inf`  — *ドキュメントは利用できません。*

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakieのみ）。

**`gap`** =  `0.2`  — バーの最終的な幅は`w * (1 - gap)`として計算され、`w`は`width`属性で決定される各バーの幅です。

**`highclip`** =  `automatic`  — カラー範囲を超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`によって表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`label_align`** =  `automatic`  — *ドキュメントは利用できません。*

**`label_color`** =  `@inherit textcolor`  — *ドキュメントは利用できません。*

**`label_font`** =  `@inherit font`  — バーラベルのフォント。

**`label_formatter`** =  `bar_label_formatter`  — *ドキュメントは利用できません。*

**`label_offset`** =  `5`  — スクリーン単位でバーの端からラベルまでの距離。`label_position = :center`の場合は適用されません。

**`label_position`** =  `:end`  — 各バーのラベルの位置。可能な値は`:end`または`:center`です。

**`label_rotation`** =  `0π`  — *ドキュメントは利用できません。*

**`label_size`** =  `@inherit fontsize`  — バーラベルのフォントサイズ。

**`lowclip`** =  `automatic`  — カラー範囲未満の任意の値の色。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは`translate!`、`rotate!`、`scale!`で行った調整を上書きします。

**`n_dodge`** =  `automatic`  — *ドキュメントは利用できません。*

**`nan_color`** =  `:transparent`  — NaN値の色。

**`offset`** =  `0.0`  — *ドキュメントは利用できません。*

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`space`** =  `:data`  — プロットを囲むボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`のときにのみ適用されます。

**`stack`** =  `automatic`  — *ドキュメントは利用できません。*

**`strokecolor`** =  `@inherit patchstrokecolor`  — *ドキュメントは利用できません。*

**`strokewidth`** =  `@inherit patchstrokewidth`  — *ドキュメントは利用できません。*

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序に依存しない透明性を使用します。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。

**`width`** =  `automatic`  — バーの隙間のない幅。`automatic`の場合、幅`w`は`minimum(diff(sort(unique(positions)))`として計算されます。バーの実際の幅は`w * (1 - gap)`として計算されます。
