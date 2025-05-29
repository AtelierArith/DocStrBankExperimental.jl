```
text(positions; text, kwargs...)
text(x, y; text, kwargs...)
text(x, y, z; text, kwargs...)
```

`text`キーワードを介して渡された1つまたは複数のテキストをプロットします。`Text`は`PointBased`変換トレイトを使用します。

## 属性

### `Text`に特有の属性

  * `color=theme(scene, :textcolor)`はテキストの色を設定します。`Vector{<:Colorant}`を渡すことで、各グリフごとに1色を設定することも、全体のテキストに1つの色を設定することもできます。色が数値のベクトルである場合、カラーマップ引数が数値を色にマッピングするために使用されます。
  * `text`は表示するテキストの1つの部分またはテキストのベクトルを指定します。数は与えられた位置の数と一致する必要があります。Makieは通常のテキストに使用される`String`と、`MathTeXEngine.jl`を使用して数式をレイアウトする`LaTeXString`をサポートしています。
  * `align::Tuple{Union{Symbol, Real}, Union{Symbol, Real}} = (:left, :bottom)`は`position`に対する文字列の整列を設定します。`:left, :center, :right, :top, :bottom, :baseline`または分数を使用します。
  * `font::Union{String, Vector{String}} = :regular`は文字列または各文字のフォントを設定します。
  * `justification::Union{Real, Symbol} = automatic`はテキストの境界ボックスに対する整列を設定します。`:left, :center, :right`または分数にできます。デフォルトでは`align`の水平方向の整列になります。
  * `rotation::Union{Real, Quaternion}`は指定された位置の周りにテキストを回転させます。
  * `fontsize::Union{Real, Vec2f}`は各文字のサイズを設定します。
  * `markerspace::Symbol = :pixel`は`fontsize`が作用する空間を設定します。可能な入力については`Makie.spaces()`を参照してください。
  * `strokewidth::Real = 0`はマーカーの周りのアウトラインの幅を設定します。
  * `strokecolor::Union{Symbol, <:Colorant} = :black`はマーカーの周りのアウトラインの色を設定します。
  * `glowwidth::Real = 0`はマーカーの周りのグロー効果のサイズを設定します。
  * `glowcolor::Union{Symbol, <:Colorant} = (:black, 0)`はグロー効果の色を設定します。
  * `word_wrap_width::Real = -1`はテキストの行幅制限を指定します。この制限を超える単語がある場合、その前に改行が挿入されます。負の数は単語の折り返しを無効にします。
  * `transform_marker::Bool = false`はモデル行列（平行移動なし）がグリフ自体に適用されるかどうかを制御します（これが真の場合、`scale!`と`rotate!`はテキストグリフに影響を与えます）。

### 色属性

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis`は数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラースケールを確認するには、`Makie.available_gradients()`を呼び出すことができます。
  * `colorscale::Function = identity`は色変換関数です。任意の関数を使用できますが、`Colorbar`と一緒に使用する場合は`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`および`Makie.Symlog10`と一緒に使用するのが最適です。
  * `colorrange::Tuple{<:Real, <:Real}`は`colormap`の開始点と終了点を表す値を設定します。
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)`は`color = NaN`の置き換え色を設定します。
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing`はカラーレンジ未満の任意の値の色を設定します。
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing`はカラーレンジを超える任意の値の色を設定します。
  * `alpha = 1.0`はカラーマップまたは色属性のアルファ値を設定します。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファがある場合、掛け算されます。

### 一般的な属性

  * `visible::Bool = true`はプロットがレンダリングされるかどうかを設定します。
  * `overdraw::Bool = false`はプロットが他のプロットの上に描画されるかどうかを設定します。これは特にGLバックエンドで深度チェックを無視することを意味します。
  * `transparency::Bool = false`はプロットが透明性をどのように扱うかを調整します。GLMakieで`transparency = true`は順序に依存しない透明性を使用する結果になります。
  * `fxaa::Bool = true`はプロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します。
  * `inspectable::Bool = true`はこのプロットが`DataInspector`によって表示されるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0`はすべての他の変換後のプロットの深度値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `model::Makie.Mat4f`はプロットのためのモデル行列を設定します。これは`translate!`、`rotate!`および`scale!`で行った調整を置き換えます。
  * `space::Symbol = :data`はボリュームプロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。
