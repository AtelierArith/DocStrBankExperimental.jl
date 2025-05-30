```
pie(values; kwargs...)
pie(point, values; kwargs...)
pie(x, y, values; kwargs...)
```

指定された `values` から円グラフを作成します。

## プロットタイプ

`pie` 関数のプロットタイプエイリアスは `Pie` です。

## 属性

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの `Plane3f` プレーンのベクターを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトではクリッププレーンは親プロットまたはシーンから継承されます。`Plane3f[]` を渡すことで親の `clip_planes` を削除できます。

**`color`** =  `:gray`  — *ドキュメントは利用できません。*

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1` の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス、GLMakieのみ）でレンダリングされるかどうかを調整します。

**`inner_radius`** =  `0`  — 円グラフセグメントの内半径です。これがゼロより大きい場合、円グラフの部分はリングセクションになります。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行った調整を上書きします。

**`normalize`** =  `true`  — `true` の場合、すべての値の合計が2π（完全な円）に正規化されます。

**`offset`** =  `0`  — 最初の円グラフセグメントの (1, 0) ベクトルからの角度オフセット（ラジアン）。

**`offset_radius`** =  `0`  — 各円グラフセグメントの中心から半径に沿ったオフセット。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`radius`** =  `1`  — 円グラフセグメントの外半径です。

**`space`** =  `:data`  — プロットを囲むボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境光遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`strokecolor`** =  `:black`  — *ドキュメントは利用できません。*

**`strokewidth`** =  `1`  — *ドキュメントは利用できません。*

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは `transparency = true` は順序独立透明性を使用する結果になります。

**`vertex_per_deg`** =  `1`  — 1度の回転に使用されるポリゴンの頂点数を制御します。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
