```
scatter(positions)
scatter(x, y)
scatter(x, y, z)
```

`(x, y, z)`, `(x, y)`、または `positions` の各要素に対してマーカーをプロットします。

## 属性

### `Scatter` に特有

  * `color=theme(scene, :markercolor)` はマーカーの色を設定します。色が設定されていない場合、`scatter!` の複数回の呼び出しは軸のカラーパレットを循環します。それ以外の場合、`Vector{<:Colorant}` を渡すことで各ポイントごとに1色を設定するか、全体の散布図に1つの色を設定できます。色が数値のベクトルである場合、カラーマップの引数が数値を色にマッピングするために使用されます。
  * `cycle::Vector{Symbol} = [:color]` は複数のプロットを作成する際に循環させる属性を設定します。
  * `marker::Union{Symbol, Char, Matrix{<:Colorant}, BezierPath, Polygon}` は散布マーカーを設定します。
  * `markersize::Union{<:Real, Vec2f} = 9` はマーカーのサイズを設定します。
  * `markerspace::Symbol = :pixel` は `markersize` が与えられる空間を設定します。可能な入力については `Makie.spaces()` を参照してください。
  * `strokewidth::Real = 0` はマーカーの周囲のアウトラインの幅を設定します。
  * `strokecolor::Union{Symbol, <:Colorant} = :black` はマーカーの周囲のアウトラインの色を設定します。
  * `glowwidth::Real = 0` はマーカーの周囲のグロー効果のサイズを設定します。
  * `glowcolor::Union{Symbol, <:Colorant} = (:black, 0)` はグロー効果の色を設定します。
  * `rotations::Union{Real, Billboard, Quaternion} = Billboard(0f0)` はマーカーの回転を設定します。`Billboard` の回転は常に深さ軸の周りです。
  * `transform_marker::Bool = false` はモデル行列（平行移動なし）がマーカー自体に適用されるかどうかを制御します。これが真の場合、`scale!` と `rotate!` はマーカーに影響を与えます。

### 色属性

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis` は数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出すことができます。
  * `colorscale::Function = identity` は色変換関数です。任意の関数を使用できますが、`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` の `Colorbar` と一緒にうまく機能します。
  * `colorrange::Tuple{<:Real, <:Real}` は `colormap` の開始点と終了点を表す値を設定します。
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)` は `color = NaN` のための置き換え色を設定します。
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing` はカラーレンジ未満の任意の値のための色を設定します。
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing` はカラーレンジを超える任意の値のための色を設定します。
  * `alpha = 1.0` はカラーマップまたは色属性のアルファ値を設定します。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファは掛け算されます。

### 一般属性

  * `visible::Bool = true` はプロットがレンダリングされるかどうかを設定します。
  * `overdraw::Bool = false` はプロットが他のプロットの上に描画されるかどうかを設定します。これは特に GL バックエンドで深さチェックを無視することを意味します。
  * `transparency::Bool = false` はプロットが透明度をどのように扱うかを調整します。GLMakie では `transparency = true` は順序に依存しない透明度を使用します。
  * `fxaa::Bool = true` はプロットが fxaa（アンチエイリアス）でレンダリングされるかどうかを調整します。
  * `inspectable::Bool = true` はこのプロットが `DataInspector` に表示されるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0` はすべての他の変換後のプロットの深さ値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1` の範囲です。これは GLMakie と WGLMakie のみに適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `model::Makie.Mat4f` はプロットのためのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行われた調整を置き換えます。
  * `space::Symbol = :data` はボリュームプロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。
