```
image(x, y, image)
image(image)
```

`x` と `y` で制約された長方形に画像をプロットします（デフォルトは画像のサイズ）。

## プロットタイプ

`image` 関数のプロットタイプエイリアスは `Image` です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファが掛け合わされます。

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの `Plane3f` プレーンのベクターを設定でき、その後ろのプロットはクリップされ（つまり、見えなくなります）、デフォルトではクリッププレーンは親プロットまたはシーンから継承されます。親の `clip_planes` を削除するには `Plane3f[]` を渡します。

**`colormap`** =  `[:black, :white]`  — 数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出します。

**`colorrange`** =  `automatic`  — `colormap` の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — カラー変換関数。任意の関数を使用できますが、`Colorbar` と一緒に使用する場合は `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` と一緒にうまく機能します。

**`depth_shift`** =  `0.0`  — すべての他の変換後のプロットの深度値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1` の範囲です。これは GLMakie と WGLMakie のみに適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `false`  — プロットが fxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakie のみ）。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector でカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspector によって生成されるデフォルトのラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`interpolate`** =  `true`  — ピクセル間で色を補間するかどうかを設定します。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`model`** =  `automatic`  — プロットのためのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行った調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN 値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特に GL バックエンドで深度チェックを無視することを意味します。

**`space`** =  `:data`  — プロットを囲むボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`ssao`** =  `false`  — プロットが ssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明度をどのように扱うかを調整します。GLMakie では `transparency = true` は順序独立透明度を使用する結果になります。

**`uv_transform`** =  `automatic`  — 画像がその長方形領域にどのようにマッピングされるかを制御する uv 座標の変換を設定します。この属性は `I`、`scale::VecTypes{2}`、`(translation::VecTypes{2}, scale::VecTypes{2})`、`:rotr90`、`:rotl90`、`:rot180`、`:swap*xy/:transpose`、`:flip*x`、`:flip*y`、`:flip*xy`、または一般的には `Makie.Mat{2, 3, Float32}` または `Makie.Mat3f`（`Makie.uv_transform()` によって返される）であることができます。タプル `(op3, op2, op1)` を渡すことで変更することもできます。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
