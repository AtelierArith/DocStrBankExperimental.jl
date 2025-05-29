```
tricontourf(triangles::Triangulation, zs; kwargs...)
tricontourf(xs, ys, zs; kwargs...)
```

`zs`の高さ情報を`xs`の水平方向の位置と`ys`の垂直方向の位置で塗りつぶされた三角形等高線をプロットします。三角形を指定するために、`xs`と`ys`の代わりにDelaunayTriangulation.jlからの`Triangulation`を提供することもできます。そうでない場合、`xs`と`ys`の無制約三角形分割が計算されます。

## 属性

### `Tricontourf`に特有

  * `levels = 10`は、n+1の等間隔のレベルで区切られたnバンドを生成する`Int`であるか、低から高までのn連続エッジをリストする`AbstractVector{<:Real}`であることができます。これによりn-1バンドが生成されます。
  * `mode = :normal`は、レベルのベクトルが解釈される方法を設定します。`:relative`に設定されている場合、各数値は`zs`の最小値と最大値の間の割合として解釈されます。例えば、`levels = 0.1:0.1:1.0`はデータの下位10%を除外します。
  * `extendlow = nothing`。これは、`minimum(zs)`から`levels`の最小値までのオプションの追加バンドの色を設定します。`:auto`の場合、カラーマップの下端が選択され、残りの色がそれに応じてシフトされます。任意の色表現の場合、この色が使用されます。`nothing`の場合、バンドは追加されません。
  * `extendhigh = nothing`。これは、`levels`の最大値から`maximum(zs)`までのオプションの追加バンドの色を設定します。`:auto`の場合、カラーマップの上端が選択され、残りの色がそれに応じてシフトされます。任意の色表現の場合、この色が使用されます。`nothing`の場合、バンドは追加されません。
  * `triangulation = DelaunayTriangulation()`。`xs`と`ys`の点が三角形分割されるモード。`DelaunayTriangulation()`を渡すと、Delaunay三角形分割が行われます。既存の三角形分割を`AbstractMatrix{<:Int}`としてサイズ(3, n)で渡すこともでき、各列は1つの三角形の頂点インデックスを指定します。または、DelaunayTriangulation.jlからの`Triangulation`として渡すこともできます。

### 一般的

  * `visible::Bool = true`は、プロットがレンダリングされるかどうかを設定します。
  * `overdraw::Bool = false`は、プロットが他のプロットの上に描画されるかどうかを設定します。これは特にGLバックエンドで深度チェックを無視することを意味します。
  * `transparency::Bool = false`は、プロットが透明度をどのように扱うかを調整します。GLMakieで`transparency = true`は、順序に依存しない透明度を使用します。
  * `fxaa::Bool = false`は、プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します。
  * `inspectable::Bool = true`は、このプロットが`DataInspector`によって表示されるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0`は、すべての他の変換後のプロットの深度値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1`。これはGLMakieとWGLMakieにのみ適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `model::Makie.Mat4f`は、プロットのモデル行列を設定します。これは`translate!`、`rotate!`、および`scale!`で行った調整を置き換えます。
  * `color`は、プロットの色を設定します。これは名前付き色`Symbol`または`Colors.Colorant`として指定できます。透明度は、`Colorant`内のアルファ値として直接含めるか、タプル`(color, alpha)`内の追加の浮動小数点数として含めることができます。色は、色の`Vector`を渡すことで各散発マーカーに設定することも、`Real`数または`Vector{<: Real}`を渡すことで`colormap`をインデックスするために使用することもできます。
  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis`は、バンドの色がサンプリングされるカラーマップを設定します。
  * `colorscale::Function = identity`は、色変換関数です。

## 属性

`MakieCore.Plot{Makie.tricontourf}`の利用可能な属性とそのデフォルトは次のとおりです：

```
  colormap       :viridis
  colorscale     identity
  edges          "nothing"
  extendhigh     "nothing"
  extendlow      "nothing"
  inspectable    true
  levels         10
  mode           :normal
  nan_color      :transparent
  transparency   false
  triangulation  Makie.DelaunayTriangulation()
```
