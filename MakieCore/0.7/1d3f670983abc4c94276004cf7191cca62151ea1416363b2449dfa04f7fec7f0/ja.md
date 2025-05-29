```
heatmap(x, y, matrix)
heatmap(x, y, func)
heatmap(matrix)
heatmap(xvector, yvector, zvector)
```

長方形の集合としてヒートマップをプロットします。`x` と `y` は、`(i, j)` が `size(matrix)` である場合、長さ `i` と `j` のいずれかであることができます。この場合、長方形はこれらのグリッドポイントの周りに配置され、ボロノイセルのようになります。`x` と `y` が不規則に間隔を空けている場合、指定されたポイントは結果として得られる長方形の中心には配置されないことに注意してください。

`x` と `y` は、長さ `i+1` と `j+1` のいずれかでもあり、この場合、長方形のエッジとして解釈されます。

長方形の色は `matrix[i, j]` から導出されます。第三引数は、`Function` (i, j) -> v であることもでき、これは `x` と `y` によって広がるグリッド上で評価されます。

もう一つの許可された形式は、3つのベクトル `xvector`、`yvector`、`zvector` を使用することです。この場合、`x` と `y` の要素のペアが二度存在しないと仮定されます。結果のグリッドから欠落しているペアは、`zvector` がその位置に `NaN` 要素を持っているかのように扱われます。

`x` と `y` が行列引数と共に省略された場合、デフォルトで `x, y = axes(matrix)` になります。

`heatmap` は `image` よりも描画が遅いため、大きくて規則的に間隔を空けたグリッドには `image` を使用することが推奨されます。

## 属性

### `Heatmap` に特有

  * `interpolate::Bool = false` は、色を補間するかどうかを設定します。

### 色の属性

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis` は、数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出すことができます。
  * `colorscale::Function = identity` は、色変換関数です。任意の関数を使用できますが、`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`、および `Makie.Symlog10` と一緒に使用する場合にのみうまく機能します。
  * `colorrange::Tuple{<:Real, <:Real}` は、`colormap` の開始点と終了点を表す値を設定します。
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)` は、`color = NaN` のための置き換え色を設定します。
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing` は、カラーレンジよりも低い値のための色を設定します。
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing` は、カラーレンジよりも高い値のための色を設定します。
  * `alpha = 1.0` は、カラーマップまたは色属性のアルファ値を設定します。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファがある場合、掛け算されます。

### 一般的な属性

  * `visible::Bool = true` は、プロットが描画されるかどうかを設定します。
  * `overdraw::Bool = false` は、プロットが他のプロットの上に描画されるかどうかを設定します。これは特に GL バックエンドでの深度チェックを無視することを意味します。
  * `transparency::Bool = false` は、プロットが透明性をどのように扱うかを調整します。GLMakie では `transparency = true` は、順序に依存しない透明性を使用する結果になります。
  * `fxaa::Bool = true` は、プロットが fxaa（アンチエイリアス）で描画されるかどうかを調整します。
  * `inspectable::Bool = true` は、このプロットが `DataInspector` に表示されるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0` は、すべての他の変換の後のプロットの深度値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1` です。これは GLMakie と WGLMakie のみに適用され、描画順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `model::Makie.Mat4f` は、プロットのモデル行列を設定します。これは `translate!`、`rotate!`、および `scale!` で行った調整を置き換えます。
  * `space::Symbol = :data` は、ボリュームプロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。
