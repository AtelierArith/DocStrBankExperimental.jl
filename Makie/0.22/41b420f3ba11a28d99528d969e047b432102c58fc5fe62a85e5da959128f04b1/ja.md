```
scatterlines(xs, ys, [zs]; kwargs...)
```

プロット `scatter` マーカーとそれらの間の `lines` を描画します。

## プロットタイプ

`scatterlines` 関数のプロットタイプエイリアスは `ScatterLines` です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファは掛け算されます。

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの `Plane3f` 平面のベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトではクリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]` を渡すことで親の `clip_planes` を削除できます。

**`color`** =  `@inherit linecolor`  — 線の色、デフォルトでは散布マーカーの色でもあります。

**`colormap`** =  `@inherit colormap :viridis`  — 数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを見るには、`Makie.available_gradients()` を呼び出します。

**`colorrange`** =  `automatic`  — `colormap` の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar` と一緒に使用する場合は `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` と一緒にうまく機能します。

**`cycle`** =  `[:color]`  — *ドキュメントは利用できません。*

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1` の範囲です。これは GLMakie と WGLMakie のみに適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `true`  — プロットが fxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakie のみ）。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector でカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspector によって生成されるデフォルトラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`joinstyle`** =  `@inherit joinstyle`  — *ドキュメントは利用できません。*

**`linecap`** =  `@inherit linecap`  — *ドキュメントは利用できません。*

**`linestyle`** =  `nothing`  — 線のパターンを設定します。例： `:solid`、 `:dot`、 `:dashdot`。カスタムパターンについては `Linestyle(Number[...])` を参照してください。

**`linewidth`** =  `@inherit linewidth`  — スクリーン単位での線の幅を設定します。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`marker`** =  `@inherit marker`  — 散布マーカーを設定します。

**`markercolor`** =  `automatic`  — *ドキュメントは利用できません。*

**`markercolormap`** =  `automatic`  — *ドキュメントは利用できません。*

**`markercolorrange`** =  `automatic`  — *ドキュメントは利用できません。*

**`markersize`** =  `@inherit markersize`  — マーカーのサイズを設定します。

**`miter_limit`** =  `@inherit miter_limit`  — *ドキュメントは利用できません。*

**`model`** =  `automatic`  — プロットのためのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行った調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN 値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特に GL バックエンドで深度チェックを無視することを意味します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`ssao`** =  `false`  — プロットが ssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`strokecolor`** =  `@inherit markerstrokecolor`  — マーカーの周りのアウトラインの色を設定します。

**`strokewidth`** =  `@inherit markerstrokewidth`  — マーカーの周りのアウトラインの幅を設定します。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakie では `transparency = true` は順序独立透明性を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。 ```
