```
lines(positions)
lines(x, y)
lines(x, y, z)
```

`(x, y, z)`, `(x, y)` または `positions` の各要素に対して接続された線プロットを作成します。

`NaN` 値は線の隙間として表示されます。

## 属性

### 特定

  * `cycle::Vector{Symbol} = [:color]` は、複数のプロットを作成する際にサイクルする属性を設定します。
  * `linestyle::Union{Nothing, Symbol, Vector} = nothing` は、線のパターンを設定します（例: `:solid`, `:dot`, `:dashdot`）。
  * `linewidth::Real = 1.5` は、ピクセル単位で線の幅を設定します。

### 一般

  * `visible::Bool = true` は、プロットがレンダリングされるかどうかを設定します。
  * `overdraw::Bool = false` は、プロットが他のプロットの上に描画されるかどうかを設定します。これは特に GL バックエンドで深度チェックを無視することを意味します。
  * `transparency::Bool = false` は、プロットが透明度をどのように扱うかを調整します。GLMakie では `transparency = true` は順序独立透明度を使用する結果になります。
  * `fxaa::Bool = false` は、プロットが fxaa（アンチエイリアス）でレンダリングされるかどうかを調整します。線プロットはすでに異なる形式のアンチエイリアスを使用していることに注意してください。
  * `inspectable::Bool = true` は、このプロットが `DataInspector` に表示されるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0` は、すべての他の変換後のプロットの深度値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1` の範囲です。これは GLMakie と WGLMakie のみに適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `model::Makie.Mat4f` は、プロットのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行った調整を置き換えます。
  * `color` は、プロットの色を設定します。名前付き色 `Symbol` または `Colors.Colorant` として指定できます。透明度は、`Colorant` のアルファ値として直接含めるか、タプル `(color, alpha)` の追加の浮動小数点数として含めることができます。色は、色の `Vector` を渡すことで線の各点に設定することも、`Real` 数または `Vector{<: Real}` を渡すことで `colormap` をインデックスするために使用することもできます。
  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis` は、数値 `color` のためにサンプリングされるカラーマップを設定します。
  * `colorrange::Tuple{<:Real, <:Real}` は、`colormap` の開始点と終了点を表す値を設定します。
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)` は、`color = NaN` のための置き換え色を設定します。
  * `space::Symbol = :data` は、線の位置の変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。
