```
surface(x, y, z)
surface(z)
```

サーフェスをプロットします。ここで、`(x, y)` は `z` のエントリの高さを定義するグリッドを定義します。`x` と `y` は、規則的なグリッドを定義する `Vectors` であるか、**または** 不規則なグリッドを定義する `Matrices` である可能性があります。

## 属性

### `Surface` に特有の属性

  * `invert_normals::Bool = false` は、サーフェスのために生成された法線を反転させます。これは、サーフェスの反対側を照らすのに役立ちます。
  * `color = nothing` は、`z` コンポーネントに依存しないサーフェスの色を設定するために `Matrix{<: Union{Number, Colorant}}` に設定できます。`color=nothing` の場合、デフォルトで `color=z` になります。

### 3D シェーディング属性

  * `shading = Makie.automatic` は、使用される照明アルゴリズムを設定します。オプションは `NoShading`（照明なし）、`FastShading`（AmbientLight + PointLight）または `MultiLightShading`（複数の光、GLMakie のみ）です。これは RPRMakie には影響しないことに注意してください。
  * `diffuse::Vec3f = Vec3f(1.0)` は、赤、緑、青のチャンネルが拡散（散乱）光にどの程度反応するかを設定します。
  * `specular::Vec3f = Vec3f(0.4)` は、オブジェクトが赤、緑、青のチャンネルで光をどの程度反射するかを設定します。
  * `shininess::Real = 32.0` は、反射がどれだけシャープであるかを設定します。
  * `backlight::Float32 = 0f0` は、反転法線を持つ二次光計算のための重みを設定します。
  * `ssao::Bool = false` は、プロットが ssao（スクリーンスペース環境遮蔽）でレンダリングされるかどうかを調整します。これは 3D プロットにのみ意味があり、`fxaa = true` の場合にのみ適用されます。

### カラー属性

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis` は、数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出すことができます。
  * `colorscale::Function = identity` は、カラー変換関数です。任意の関数を使用できますが、`Colorbar` と一緒に `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` と一緒にうまく機能します。
  * `colorrange::Tuple{<:Real, <:Real}` は、`colormap` の開始点と終了点を表す値を設定します。
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)` は、`color = NaN` のための置き換え色を設定します。
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing` は、カラーレンジ未満の任意の値のための色を設定します。
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing` は、カラーレンジを超える任意の値のための色を設定します。
  * `alpha = 1.0` は、カラーマップまたはカラー属性のアルファ値を設定します。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファがある場合、掛け算されます。

### 一般的な属性

  * `visible::Bool = true` は、プロットがレンダリングされるかどうかを設定します。
  * `overdraw::Bool = false` は、プロットが他のプロットの上に描画されるかどうかを設定します。これは特に GL バックエンドで深度チェックを無視することを意味します。
  * `transparency::Bool = false` は、プロットが透明性をどのように扱うかを調整します。GLMakie では `transparency = true` は順序独立透明性を使用する結果になります。
  * `fxaa::Bool = true` は、プロットが fxaa（アンチエイリアス）でレンダリングされるかどうかを調整します。
  * `inspectable::Bool = true` は、このプロットが `DataInspector` に表示されるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0` は、すべての他の変換後のプロットの深度値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1` です。これは GLMakie と WGLMakie のみに適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `model::Makie.Mat4f` は、プロットのためのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行った調整を置き換えます。
  * `space::Symbol = :data` は、ボリュームプロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。
