```
tooltip(position, string)
tooltip(x, y, string)
```

`position`を指すツールチップを作成し、指定された`string`を表示します。

## プロットタイプ

`tooltip`関数のプロットタイプエイリアスは`Tooltip`です。

## 属性

**`align`** =  `0.5`  — ツールチップの位置を`position`に対して整列させます。`align = 0.5`の場合、ツールチップは`position`の上/下/左/右に中央に配置されます。

**`backgroundcolor`** =  `:white`  — ツールチップの背景色を設定します。

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`プレーンのベクトルを設定でき、その後ろのプロットはクリップされます（つまり、見えなくなります）。デフォルトでは、クリッププレーンは親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`depth_shift`** =  `0.0`  — すべての他の変換後のプロットの深度値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`font`** =  `@inherit font`  — フォントを設定します。

**`fontsize`** =  `16`  — スクリーン単位でのテキストサイズを設定します。

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakieのみ）。

**`inspectable`** =  `false`  — このプロットが`DataInspector`で表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`justification`** =  `:left`  — テキストがそのバウンディングボックス内で`:left`、`:center`、または`:right`に整列されるかどうかを設定します。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは`translate!`、`rotate!`、および`scale!`で行った調整を上書きします。

**`offset`** =  `10`  — 指定された`position`とその位置を指す三角形の先端との間のオフセットを設定します。

**`outline_color`** =  `:black`  — ツールチップのアウトラインの色を設定します。

**`outline_linestyle`** =  `nothing`  — ツールチップのアウトラインの線スタイルを設定します。

**`outline_linewidth`** =  `2.0`  — ツールチップのアウトラインの線幅を設定します。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`placement`** =  `:above`  — ツールチップが`position`に対してどこに配置されるべきかを設定します。`:above`、`:below`、`:left`、`:right`のいずれかです。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`の場合にのみ適用されます。

**`strokecolor`** =  `:white`  — テキストのアウトラインの色を設定します。

**`strokewidth`** =  `0`  — 正の値に設定すると、テキストにアウトラインが付けられます。

**`text`** =  `""`  — *ドキュメントは利用できません。*

**`textcolor`** =  `@inherit textcolor`  — テキストの色を設定します。

**`textpadding`** =  `(4, 4, 4, 4)`  — ツールチップ内のテキストの周りのパディングを設定します。これは`(left, right, bottom, top)`のオフセットとして与えられます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序独立透明性を使用する結果になります。

**`triangle_size`** =  `10`  — `position`を指す三角形のサイズを設定します。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。

**`xautolimits`** =  `false`  — *ドキュメントは利用できません。*

**`yautolimits`** =  `false`  — *ドキュメントは利用できません。*

**`zautolimits`** =  `false`  — *ドキュメントは利用できません。* ```
