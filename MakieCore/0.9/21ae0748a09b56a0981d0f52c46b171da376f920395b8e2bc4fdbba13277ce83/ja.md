```
heatmap(x, y, matrix)
heatmap(x, y, func)
heatmap(matrix)
heatmap(xvector, yvector, zvector)
```

矩形の集合としてヒートマップをプロットします。`x` と `y` は、`(i, j)` が `size(matrix)` である場合、長さ `i` と `j` であることができます。この場合、矩形はこれらのグリッドポイントの周りに配置され、ボロノイセルのようになります。`x` と `y` が不規則に間隔を空けている場合、指定されたポイントは結果の矩形の中心には配置されません。

`x` と `y` は、長さ `i+1` と `j+1` であることもでき、この場合、矩形のエッジとして解釈されます。

矩形の色は `matrix[i, j]` から導出されます。第三の引数は、`Function` (i, j) -> v であることもでき、これは `x` と `y` によって広がるグリッド上で評価されます。

別の許可された形式は、3つのベクトル `xvector`、`yvector`、`zvector` を使用することです。この場合、`x` と `y` の要素のペアが二度存在しないと仮定されます。結果のグリッドから欠落しているペアは、`zvector` がその位置に `NaN` 要素を持っているかのように扱われます。

`x` と `y` が行列引数と共に省略された場合、デフォルトで `x, y = axes(matrix)` になります。

`heatmap` は `image` よりも描画が遅いため、大きくて規則的に間隔を空けたグリッドには `image` を使用することが推奨されます。

## プロットタイプ

`heatmap` 関数のプロットタイプエイリアスは `Heatmap` です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファがある場合、掛け算されます。

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの `Plane3f` プレーンのベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリッププレーンは親プロットまたはシーンから継承されます。`Plane3f[]` を渡すことで親の `clip_planes` を削除できます。

**`colormap`** =  `@inherit colormap :viridis`  — 数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap` の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar` と一緒に使用する場合は `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`、および `Makie.Symlog10` と一緒にうまく機能します。

**`depth_shift`** =  `0.0`  — 他のすべての変換の後にプロットの深度値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1` の範囲です。これは GLMakie と WGLMakie のみに適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `true`  — プロットが fxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakie のみ）。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector でカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspector によって生成されるデフォルトラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`interpolate`** =  `false`  — 色が補間されるべきかどうかを設定します。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは `translate!`、`rotate!`、および `scale!` で行った調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN 値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特に GL バックエンドで深度チェックを無視することを意味します。

**`space`** =  `:data`  — プロットを囲むボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`ssao`** =  `false`  — プロットが ssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakie では `transparency = true` は順序独立透明性を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
