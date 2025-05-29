```
volumeslices(x, y, z, v)
```

ボリューム v のヒートマップスライスを描画します。

## プロットタイプ

`volumeslices` 関数のプロットタイプエイリアスは `VolumeSlices` です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたはカラー属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファは掛け算されます。

**`bbox_color`** =  `RGBAf(0.5, 0.5, 0.5, 0.5)`  — *ドキュメントは利用できません。*

**`bbox_visible`** =  `true`  — *ドキュメントは利用できません。*

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの `Plane3f` プレーンのベクターを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトではクリッププレーンは親プロットまたはシーンから継承されます。`Plane3f[]` を渡すことで親の `clip_planes` を削除できます。

**`colormap`** =  `@inherit colormap :viridis`  — 数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出します。

**`colorrange`** =  `automatic`  — `colormap` の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — カラー変換関数。任意の関数を使用できますが、`Colorbar` と一緒に `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` と一緒にうまく機能します。

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深さ値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1` の範囲です。これは GLMakie と WGLMakie のみに適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `true`  — プロットが fxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakie のみ）。

**`highclip`** =  `automatic`  — カラー範囲を超える任意の値のための色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector でカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspector によって生成されるデフォルトのラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`interpolate`** =  `false`  — 色が補間されるべきかどうかを設定します。

**`lowclip`** =  `automatic`  — カラー範囲未満の任意の値のための色。

**`model`** =  `automatic`  — プロットのためのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN 値のための色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特に GL バックエンドで深さチェックを無視することを意味します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`ssao`** =  `false`  — プロットが ssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明度をどのように扱うかを調整します。GLMakie では `transparency = true` は順序独立透明度を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
