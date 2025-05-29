```
poly(vertices, indices; kwargs...)
poly(points; kwargs...)
poly(shape; kwargs...)
poly(mesh; kwargs...)
```

与えられた引数に基づいてポリゴンをプロットします。頂点とインデックスが与えられた場合、`mesh`と同様に機能します。ポイントが与えられた場合、すべてのポイントを順番に接続する1つのポリゴンを描画します。形状が与えられた場合（本質的に`GeometryBasics`によって分解可能なもの）、`decompose(shape)`をプロットします。

```
poly(coordinates, connectivity; kwargs...)
```

ポリゴンをプロットします。ポリゴンは`coordinates`（頂点の座標）と`connectivity`（頂点間のエッジ）によって定義されます。

## 属性

### `Poly`に特有の属性

  * `color=theme(scene, :patchcolor)`はポリゴンの色を設定します。頂点ごとの色のための`Vector{<:Colorant}`または単一の`Colorant`であることができます。テクスチャを使用してメッシュに色を付けるために`Matrix{<:Colorant}`を使用することができ、これはメッシュがテクスチャ座標を含む必要があります。数値のベクトルまたは行列も使用でき、これにより数値を色にマッピングするためのカラーマップ引数が使用されます。また、`Makie.LinePattern`を使用してポリゴンに通常のストロークパターンを適用することもできます。
  * `strokecolor::Union{Symbol, <:Colorant} = :black`はマーカーの周囲のアウトラインの色を設定します。
  * `strokecolormap`::Union{Symbol, Vector{<:Colorant}} = :viridis`は数値`color`のためにサンプリングされるカラーマップを設定します。
  * `strokewidth::Real = 0`はマーカーの周囲のアウトラインの幅を設定します。
  * `linestyle::Union{Nothing, Symbol, Vector} = nothing`は線のパターンを設定します（例：`:solid`, `:dot`, `:dashdot`）。

### 色属性

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis`は数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できます。また、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラースケールを確認するには、`Makie.available_gradients()`を呼び出すことができます。
  * `colorscale::Function = identity`は色変換関数です。任意の関数を使用できますが、`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`、および`Makie.Symlog10`と一緒に使用する場合にのみうまく機能します。
  * `colorrange::Tuple{<:Real, <:Real}`は`colormap`の開始点と終了点を表す値を設定します。
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)`は`color = NaN`のための置き換え色を設定します。
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing`はカラーレンジ未満の任意の値のための色を設定します。
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing`はカラーレンジを超える任意の値のための色を設定します。
  * `alpha = 1.0`はカラーマップまたは色属性のアルファ値を設定します。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファがある場合、掛け算されます。

### 一般属性

  * `visible::Bool = true`はプロットがレンダリングされるかどうかを設定します。
  * `overdraw::Bool = false`はプロットが他のプロットの上に描画されるかどうかを設定します。これは特にGLバックエンドで深度チェックを無視することを意味します。
  * `transparency::Bool = false`はプロットが透明性をどのように扱うかを調整します。GLMakieで`transparency = true`は順序に依存しない透明性を使用する結果になります。
  * `fxaa::Bool = true`はプロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します。
  * `inspectable::Bool = true`はこのプロットが`DataInspector`によって表示されるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0`はすべての他の変換後のプロットの深度値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1`です。これはGLMakieおよびWGLMakieにのみ適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `model::Makie.Mat4f`はプロットのモデル行列を設定します。これは`translate!`、`rotate!`、および`scale!`で行った調整を置き換えます。
  * `space::Symbol = :data`はボリュームプロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。
