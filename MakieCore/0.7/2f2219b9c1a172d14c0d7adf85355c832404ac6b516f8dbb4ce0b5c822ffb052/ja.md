```
lines(positions)
lines(x, y)
lines(x, y, z)
```

`(x, y, z)`, `(x, y)` または `positions` の各要素に対して接続された線プロットを作成します。

`NaN` 値は線の隙間として表示されます。

## 属性

### `Lines` に特有

  * `color=theme(scene, :linecolor)` は線の色を設定します。色が設定されていない場合、`line!` への複数の呼び出しは軸のカラーパレットを循環します。それ以外の場合、`Vector{<:Colorant}` を渡すことで各線のポイントごとに色を設定するか、全体の線に対して1つの色を設定できます。色が数値のベクトルである場合、カラーマップの引数が数値を色にマッピングするために使用されます。
  * `cycle::Vector{Symbol} = [:color]` は複数のプロットを作成する際に循環させる属性を設定します。
  * `linestyle::Union{Nothing, Symbol, Linestyle} = nothing` は線のパターンを設定します。例: `:solid`, `:dot`, `:dashdot`。カスタムパターンについては `Linestyle(Number[...])` を参照してください。
  * `linewidth::Union{Real, Vector} = 1.5` は線の幅をピクセル単位で設定します。

### 色属性

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis` は数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出すことができます。
  * `colorscale::Function = identity` は色変換関数です。任意の関数を使用できますが、`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` と一緒に使用する場合にのみうまく機能します。
  * `colorrange::Tuple{<:Real, <:Real}` は `colormap` の開始点と終了点を表す値を設定します。
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)` は `color = NaN` のための置き換え色を設定します。
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing` はカラーレンジ未満の任意の値のための色を設定します。
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing` はカラーレンジを超える任意の値のための色を設定します。
  * `alpha = 1.0` はカラーマップまたは色属性のアルファ値を設定します。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファは乗算されます。

### 一般属性

  * `visible::Bool = true` はプロットがレンダリングされるかどうかを設定します。
  * `overdraw::Bool = false` はプロットが他のプロットの上に描画されるかどうかを設定します。これは特に GL バックエンドで深度チェックを無視することを意味します。
  * `transparency::Bool = false` はプロットが透明度をどのように扱うかを調整します。GLMakie では `transparency = true` は順序に依存しない透明度を使用します。
  * `fxaa::Bool = true` はプロットが fxaa（アンチエイリアス）でレンダリングされるかどうかを調整します。
  * `inspectable::Bool = true` はこのプロットが `DataInspector` に表示されるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0` はすべての他の変換後のプロットの深度値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1` の範囲です。これは GLMakie と WGLMakie のみに適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `model::Makie.Mat4f` はプロットのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行った調整を置き換えます。
  * `space::Symbol = :data` はボリュームプロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。
