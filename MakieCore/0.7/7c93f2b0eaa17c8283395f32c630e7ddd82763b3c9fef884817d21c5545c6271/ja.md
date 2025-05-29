```
mesh(x, y, z)
mesh(mesh_object)
mesh(x, y, z, faces)
mesh(xyz, faces)
```

3Dまたは2Dメッシュをプロットします。サポートされている`mesh_object`には、[GeometryBasics.jl](https://github.com/JuliaGeometry/GeometryBasics.jl)の`Mesh`タイプが含まれます。

## 属性

### `Mesh`に特有の属性

  * `color=theme(scene, :patchcolor)`はメッシュの色を設定します。頂点ごとの色のための`Vector{<:Colorant}`または単一の`Colorant`であることができます。テクスチャでメッシュに色を付けるために`Matrix{<:Colorant}`を使用することができ、これはメッシュがテクスチャ座標を含む必要があります。数値のベクトルまたは行列も使用でき、これにより数値を色にマッピングするためのカラーマップ引数が使用されます。
  * `interpolate::Bool = false`は色を補間するかどうかを設定します。

### 3Dシェーディング属性

  * `shading = Makie.automatic`は使用される照明アルゴリズムを設定します。オプションは`NoShading`（照明なし）、`FastShading`（AmbientLight + PointLight）または`MultiLightShading`（複数の光源、GLMakieのみ）です。これはRPRMakieには影響しないことに注意してください。
  * `diffuse::Vec3f = Vec3f(1.0)`は赤、緑、青のチャンネルが拡散（散乱）光にどの程度反応するかを設定します。
  * `specular::Vec3f = Vec3f(0.4)`はオブジェクトが赤、緑、青のチャンネルで光をどの程度反射するかを設定します。
  * `shininess::Real = 32.0`は反射の鋭さを設定します。
  * `backlight::Float32 = 0f0`は反転法線を使用した二次光計算の重みを設定します。
  * `ssao::Bool = false`はプロットがssao（スクリーンスペース環境遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`と一緒にのみ適用されます。

### カラー属性

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis`は数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。
  * `colorscale::Function = identity`は色変換関数です。任意の関数を使用できますが、`Colorbar`と一緒に`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`および`Makie.Symlog10`と一緒にうまく機能します。
  * `colorrange::Tuple{<:Real, <:Real}`は`colormap`の開始点と終了点を表す値を設定します。
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)`は`color = NaN`のための置き換え色を設定します。
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing`はカラーレンジ未満の任意の値のための色を設定します。
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing`はカラーレンジを超える任意の値のための色を設定します。
  * `alpha = 1.0`はカラーマップまたは色属性のアルファ値を設定します。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファは乗算されます。

### 一般的な属性

  * `visible::Bool = true`はプロットがレンダリングされるかどうかを設定します。
  * `overdraw::Bool = false`はプロットが他のプロットの上に描画されるかどうかを設定します。これは具体的にはGLバックエンドで深度チェックを無視することを意味します。
  * `transparency::Bool = false`はプロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序に依存しない透明性を使用する結果になります。
  * `fxaa::Bool = true`はプロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します。
  * `inspectable::Bool = true`はこのプロットが`DataInspector`によって表示されるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0`はすべての他の変換の後のプロットの深度値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1`です。これはGLMakieおよびWGLMakieにのみ適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `model::Makie.Mat4f`はプロットのモデル行列を設定します。これは`translate!`、`rotate!`および`scale!`で行った調整を置き換えます。
  * `space::Symbol = :data`はボリュームプロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。
