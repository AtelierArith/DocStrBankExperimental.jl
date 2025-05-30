```
qqnorm(y; kwargs...)
```

`qqplot(Normal(0,1), y)`の省略形であり、すなわち、`y`のQ-Qプロットを標準正規分布に対して描画します。詳細については`qqplot`を参照してください。

## プロットタイプ

`qqnorm`関数のプロットタイプエイリアスは`QQNorm`です。

## 属性

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`プレーンのベクトルを設定でき、その背後でプロットがクリップされます（すなわち、見えなくなります）。デフォルトでは、クリッププレーンは親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`color`** =  `@inherit linecolor`  — 線とマーカーの色を制御します（`markercolor`が指定されていない場合）。

**`cycle`** =  `[:color]`  — *ドキュメントは利用できません。*

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深さ値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakieのみ）。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`によって表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`linestyle`** =  `nothing`  — *ドキュメントは利用できません。*

**`linewidth`** =  `@inherit linewidth`  — *ドキュメントは利用できません。*

**`marker`** =  `@inherit marker`  — *ドキュメントは利用できません。*

**`markercolor`** =  `automatic`  — *ドキュメントは利用できません。*

**`markersize`** =  `@inherit markersize`  — *ドキュメントは利用できません。*

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは`translate!`、`rotate!`、および`scale!`で行った調整を上書きします。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深さチェックを無視することを意味します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`のときにのみ適用されます。

**`strokecolor`** =  `@inherit markerstrokecolor`  — *ドキュメントは利用できません。*

**`strokewidth`** =  `@inherit markerstrokewidth`  — *ドキュメントは利用できません。*

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序に依存しない透明性を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
