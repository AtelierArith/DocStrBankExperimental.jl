```
violin(x, y)
```

バイオリンプロットを描画します。

## 引数

  * `x`: カテゴリの位置
  * `y`: 密度が計算される変数

## プロットタイプ

`violin` 関数のプロットタイプエイリアスは `Violin` です。

## 属性

**`bandwidth`** =  `automatic`  — *ドキュメントはありません。*

**`boundary`** =  `automatic`  — *ドキュメントはありません。*

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの `Plane3f` プレーンのベクターを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトではクリッププレーンは親プロットまたはシーンから継承されます。`Plane3f[]` を渡すことで親の `clip_planes` を削除できます。

**`color`** =  `@inherit patchcolor`  — *ドキュメントはありません。*

**`cycle`** =  `[:color => :patchcolor]`  — *ドキュメントはありません。*

**`datalimits`** =  `(-Inf, Inf)`  — `violin` をトリミングする値を指定します。`Tuple` または `Function`（例: `datalimits=extrema`）であることができます。

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深さ値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1` の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`dodge`** =  `automatic`  — *ドキュメントはありません。*

**`dodge_gap`** =  `0.03`  — *ドキュメントはありません。*

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakieのみ）。

**`gap`** =  `0.2`  — 縮小係数、`width -> width * (1 - gap)`。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`max_density`** =  `automatic`  — *ドキュメントはありません。*

**`mediancolor`** =  `@inherit linecolor`  — *ドキュメントはありません。*

**`medianlinewidth`** =  `@inherit linewidth`  — *ドキュメントはありません。*

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは `translate!`、`rotate!`、および `scale!` で行われた調整を上書きします。

**`n_dodge`** =  `automatic`  — *ドキュメントはありません。*

**`npoints`** =  `200`  — *ドキュメントはありません。*

**`orientation`** =  `:vertical`  — バイオリンの向き（`:vertical` または `:horizontal`）

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深さチェックを無視することを意味します。

**`scale`** =  `:area`  — 面積（`:area`）、カウント（`:count`）、または幅（`:width`）で密度をスケールします。

**`show_median`** =  `false`  — 中央値を中線として表示します。

**`side`** =  `:both`  — バイオリンを片側のみにプロットするために `:left` または `:right` を指定します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`strokecolor`** =  `@inherit patchstrokecolor`  — *ドキュメントはありません。*

**`strokewidth`** =  `@inherit patchstrokewidth`  — *ドキュメントはありません。*

**`transformation`** =  `:automatic`  — *ドキュメントはありません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは `transparency = true` は順序独立透明性を使用します。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。

**`weights`** =  `automatic`  — 統計的重みのベクター（データの長さ）。デフォルトでは、各観測値の重みは `1` です。

**`width`** =  `automatic`  — 縮小前のボックスの幅。
