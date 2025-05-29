```
linesegments(positions)
linesegments(vector_of_2tuples_of_points)
linesegments(x, y)
linesegments(x, y, z)
```

`(x, y, z)`、`(x, y)`、または`positions`の各点のペアに対して線を描画します。

## 属性

### `LineSegments`に特有

  * `color=theme(scene, :linecolor)`は、ラインセグメントの色を設定します。色が設定されていない場合、`linesegments!`への複数の呼び出しは軸のカラーパレットを循環します。そうでない場合、`Vector{<:Colorant}`を渡すことで各ラインポイントごとに1色、または各ラインセグメントごとに1色を設定できます。色が数値のベクトルである場合、カラーマップ引数が数値を色にマッピングするために使用されます。
  * `cycle::Vector{Symbol} = [:color]`は、複数のプロットを作成する際に循環させる属性を設定します。
  * `linestyle::Union{Nothing, Symbol, Vector} = nothing`は、ラインのパターンを設定します（例：`:solid`、`:dot`、`:dashdot`）。
  * `linewidth::Union{Real, Vector} = 1.5`は、ピクセル単位でのラインの幅を設定します。

### 色属性

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis`は、数値の`color`に対してサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。
  * `colorscale::Function = identity`は、色変換関数です。任意の関数を使用できますが、`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`、および`Makie.Symlog10`と一緒に使用する場合にのみうまく機能します。
  * `colorrange::Tuple{<:Real, <:Real}`は、`colormap`の開始点と終了点を表す値を設定します。
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)`は、`color = NaN`の置き換え色を設定します。
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing`は、カラーレンジ未満の任意の値に対する色を設定します。
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing`は、カラーレンジを超える任意の値に対する色を設定します。
  * `alpha = 1.0`は、カラーマップまたは色属性のアルファ値を設定します。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファがある場合、掛け算されます。

### 一般的な属性

  * `visible::Bool = true`は、プロットがレンダリングされるかどうかを設定します。
  * `overdraw::Bool = false`は、プロットが他のプロットの上に描画されるかどうかを設定します。これは特にGLバックエンドで深度チェックを無視することを意味します。
  * `transparency::Bool = false`は、プロットが透明性をどのように扱うかを調整します。GLMakieで`transparency = true`は、順序に依存しない透明性を使用する結果になります。
  * `fxaa::Bool = true`は、プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します。
  * `inspectable::Bool = true`は、このプロットが`DataInspector`によって表示されるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0`は、すべての他の変換後のプロットの深度値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `model::Makie.Mat4f`は、プロットのモデル行列を設定します。これは`translate!`、`rotate!`、および`scale!`で行った調整を置き換えます。
  * `space::Symbol = :data`は、ボリュームプロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。
