```
tricontourf(triangles::Triangulation, zs; kwargs...)
tricontourf(xs, ys, zs; kwargs...)
```

`zs`の高さ情報を`xs`の水平方向の位置と`ys`の垂直方向の位置で塗りつぶした三角輪郭をプロットします。三角形を指定するために、`xs`と`ys`の代わりにDelaunayTriangulation.jlからの`Triangulation`を提供することもできます。そうでない場合、`xs`と`ys`の無制約三角形分割が計算されます。

## プロットタイプ

`tricontourf`関数のプロットタイプエイリアスは`Tricontourf`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`平面のベクトルを設定でき、その後ろのプロットはクリップされます（つまり、見えなくなります）。デフォルトでは、クリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`colormap`** =  `@inherit colormap`  — バンドの色がサンプリングされるカラーマップを設定します。

**`colorscale`** =  `identity`  — 色変換関数

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深さ値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieとWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`edges`** =  `nothing`  — *ドキュメントは利用できません。*

**`extendhigh`** =  `nothing`  — これは、`levels`の最高値から`maximum(zs)`までのオプションの追加バンドの色を設定します。`:auto`の場合、カラーマップの高い端が選択され、残りの色がそれに応じてシフトされます。任意の色表現の場合、この色が使用されます。`nothing`の場合、バンドは追加されません。

**`extendlow`** =  `nothing`  — これは、`minimum(zs)`から`levels`の最低値までのオプションの追加バンドの色を設定します。`:auto`の場合、カラーマップの低い端が選択され、残りの色がそれに応じてシフトされます。任意の色表現の場合、この色が使用されます。`nothing`の場合、バンドは追加されません。

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス、GLMakieのみ）でレンダリングされるかどうかを調整します。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`によって表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`levels`** =  `10`  — `Int`であり、n+1の等間隔のレベルで区切られたnバンドを生成するか、低から高までのn個の連続したエッジをリストする`AbstractVector{<:Real}`であることができます。これによりn-1バンドが生成されます。

**`mode`** =  `:normal`  — レベルのベクトルが解釈される方法を設定します。`:relative`に設定されている場合、各数値は`zs`の最小値と最大値の間の割合として解釈されます。たとえば、`levels = 0.1:0.1:1.0`はデータの下位10%を除外します。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは`translate!`、`rotate!`、および`scale!`で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — *ドキュメントは利用できません。*

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深さチェックを無視することを意味します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`の場合にのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序に依存しない透明性を使用します。

**`triangulation`** =  `DelaunayTriangulation()`  — `xs`と`ys`の点が三角形分割されるモード。`DelaunayTriangulation()`を渡すとDelaunay三角形分割が行われます。また、サイズ(3, n)の`AbstractMatrix{<:Int}`として既存の三角形分割を渡すこともでき、各列は1つの三角形の頂点インデックスを指定します。またはDelaunayTriangulation.jlからの`Triangulation`として渡すこともできます。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
