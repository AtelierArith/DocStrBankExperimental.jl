```
contourf_fast(X; kwargs...)
```

ピクセルが十分小さい場合、`contourf()`と同じ出力を生成するはずですが、より高速です。`contourf_fast()`は入力データを量子化し、`contourf()`のように明示的な輪郭を見つけるのではなく、画像として表示します。

## プロットタイプ

`contourf_fast`関数のプロットタイプエイリアスは`Contourf_Fast`です。

## 属性

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`プレーンのベクターを設定でき、その背後でプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリッププレーンは親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`colormap`** =  `@inherit colormap`  — *ドキュメントは利用できません。*

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`extendhigh`** =  `nothing`  — *ドキュメントは利用できません。*

**`extendlow`** =  `nothing`  — *ドキュメントは利用できません。*

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス、GLMakieのみ）でレンダリングされるかどうかを調整します。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`によって表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`levels`** =  `10`  — *ドキュメントは利用できません。*

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは`translate!`、`rotate!`、および`scale!`で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — *ドキュメントは利用できません。*

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`の場合にのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序に依存しない透明性を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
