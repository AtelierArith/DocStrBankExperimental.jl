```
contourf(xs, ys, zs; kwargs...)
```

`zs`の高さ情報を`xs`の水平グリッド位置と`ys`の垂直グリッド位置で塗りつぶした等高線をプロットします。

`xs`と`ys`は、直交グリッドの場合はベクトル、曲線グリッドの場合は行列であり、[`surface`](@ref)が動作するのと同様です。

## プロットタイプ

`contourf`関数のプロットタイプエイリアスは`Contourf`です。

## 属性

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`平面のベクトルを設定でき、その後ろのプロットはクリップされます（つまり、見えなくなります）。デフォルトでは、クリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`colormap`** =  `@inherit colormap`  — *ドキュメントは利用できません。*

**`colorscale`** =  `identity`  — *ドキュメントは利用できません。*

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深さ値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`extendhigh`** =  `nothing`  — `:normal`モードでは、高いエッジから`Inf`までのバンドを表示したい場合、`extendhigh`を`:auto`に設定すると、拡張部分が最後のレベルと同じ色になります。または、色を直接指定できます（デフォルトの`nothing`は拡張バンドなしを意味します）。

**`extendlow`** =  `nothing`  — `:normal`モードでは、`-Inf`から低いエッジまでのバンドを表示したい場合、`extendlow`を`:auto`に設定すると、拡張部分が最初のレベルと同じ色になります。または、色を直接指定できます（デフォルトの`nothing`は拡張バンドなしを意味します）。

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakieのみ）。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`で表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`levels`** =  `10`  — 次のいずれかであることができます。

  * n等幅のレベルまたはバンドを生成する`Int`
  * 低い値から高い値までのn連続エッジをリストする`AbstractVector{<:Real}`、これによりn-1レベルまたはバンドが生成されます

`levels`が`Int`の場合、contourfプロットはすべての`zs`値が端から端までカバーされるため、長方形になります。これが、`Axis`がそのようなcontourfプロットに対してタイトな制限をデフォルトで持つ理由です。しかし、`levels`を`AbstractVector{<:Real}`として指定した場合、contourfプロットは不規則な形状を持つ可能性があるため、軸の制限にはデフォルトのマージンが含まれることに注意してください。`tightlimits!(ax)`を使用して、`Int`の動作に似た制限を厳しくすることができます。

**`mode`** =  `:normal`  — `levels`属性がどのように解釈されるかを決定します。`:normal`または`:relative`のいずれかです。`:normal`モードでは、レベルはz値に直接対応します。`:relative`モードでは、`zs`の最小値と最大値の間の割合でエッジを指定します。たとえば、`levels = 0.1:0.1:1.0, mode = :relative`を使用して、下位10%を除外しながら上位90%のバンドを描画するために使用できます。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは、`translate!`、`rotate!`、および`scale!`で行った調整を上書きします。

**`nan_color`** =  `:transparent`  — *ドキュメントは利用できません。*

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは具体的には、GLバックエンドでの深度チェックを無視することを意味します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境光遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`と一緒にのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明度をどのように扱うかを調整します。GLMakieでは、`transparency = true`は順序に依存しない透明度を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。 ```
