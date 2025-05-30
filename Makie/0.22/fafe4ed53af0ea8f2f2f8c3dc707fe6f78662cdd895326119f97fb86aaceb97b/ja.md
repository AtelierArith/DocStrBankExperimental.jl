```
stem(xs, ys, [zs]; kwargs...)
```

指定された位置にマーカーをプロットし、`offset` からステムラインに沿って延長します。

`stem` の変換特性は `PointBased` です。

## プロットタイプ

`stem` 関数のプロットタイプエイリアスは `Stem` です。

## 属性

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの `Plane3f` 平面のベクターを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトではクリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]` を渡すことで親の `clip_planes` を削除できます。

**`color`** =  `@inherit markercolor`  — *ドキュメントは利用できません。*

**`colormap`** =  `@inherit colormap`  — *ドキュメントは利用できません。*

**`colorrange`** =  `automatic`  — *ドキュメントは利用できません。*

**`colorscale`** =  `identity`  — *ドキュメントは利用できません。*

**`cycle`** =  `[[:stemcolor, :color, :trunkcolor] => :color]`  — *ドキュメントは利用できません。*

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深さ値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1` の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス、GLMakieのみ）でレンダリングされるかどうかを調整します。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`marker`** =  `:circle`  — *ドキュメントは利用できません。*

**`markersize`** =  `@inherit markersize`  — *ドキュメントは利用できません。*

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行った調整を上書きします。

**`offset`** =  `0`  — 数字である場合、2Dの場合は `y` を、3Dの場合は `z` を設定します。2Dプロットの場合は `Point2`、3Dプロットの場合は `Point3` であることもできます。また、`xs`、`ys`、`zs` と同じ長さのこれらのいずれかのイテラブルであることもできます。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深さチェックを無視することを意味します。

**`space`** =  `:data`  — プロットを囲むボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`stemcolor`** =  `@inherit linecolor`  — *ドキュメントは利用できません。*

**`stemcolormap`** =  `@inherit colormap`  — *ドキュメントは利用できません。*

**`stemcolorrange`** =  `automatic`  — *ドキュメントは利用できません。*

**`stemlinestyle`** =  `nothing`  — *ドキュメントは利用できません。*

**`stemwidth`** =  `@inherit linewidth`  — *ドキュメントは利用できません。*

**`strokecolor`** =  `@inherit markerstrokecolor`  — *ドキュメントは利用できません。*

**`strokewidth`** =  `@inherit markerstrokecolor`  — *ドキュメントは利用できません。*

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは `transparency = true` は順序に依存しない透明性を使用します。

**`trunkcolor`** =  `@inherit linecolor`  — *ドキュメントは利用できません。*

**`trunkcolormap`** =  `@inherit colormap`  — *ドキュメントは利用できません。*

**`trunkcolorrange`** =  `automatic`  — *ドキュメントは利用できません。*

**`trunklinestyle`** =  `nothing`  — *ドキュメントは利用できません。*

**`trunkwidth`** =  `@inherit linewidth`  — *ドキュメントは利用できません。*

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。 ```
