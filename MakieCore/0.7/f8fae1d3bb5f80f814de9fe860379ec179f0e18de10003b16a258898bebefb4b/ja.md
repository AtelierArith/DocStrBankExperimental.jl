```
meshscatter(positions)
meshscatter(x, y)
meshscatter(x, y, z)
```

`(x, y, z)`、`(x, y)`、または `positions` の各要素に対してメッシュをプロットします（`scatter` に似ています）。`markersize` は、渡されたプリミティブに適用されるスケーリングです。

## 属性

### `MeshScatter` に特有

  * `color = theme(scene, :markercolor)` はマーカーの色を設定します。色が設定されていない場合、`meshscatter!` の複数回の呼び出しは軸のカラーパレットを循環します。そうでない場合、`Vector{<:Colorant}` を渡すことで各ポイントごとに1色を設定するか、全体のメッシュスキャッタープロットに1つのカラントを設定できます。色が数値のベクトルである場合、カラーマップ引数が数値を色にマッピングするために使用されます。
  * `cycle::Vector{Symbol} = [:color]` は、複数のプロットを作成する際に循環させる属性を設定します。
  * `marker::Union{Symbol, GeometryBasics.GeometryPrimitive, GeometryBasics.Mesh}` は散布されたメッシュを設定します。
  * `markersize::Union{<:Real, Vec3f} = 0.1` はメッシュのスケールを設定します。これは、各散布メッシュに個別に適用するためにベクトルとして指定できます。
  * `rotations::Union{Real, Vec3f, Quaternion} = 0` はメッシュの回転を設定します。数値の回転は z 軸の周りで、`Vec3f` はメッシュがそのベクトルになるように回転し、クォータニオンは一般的な回転を説明します。これは、各散布メッシュに個別に適用するためにベクトルとして指定できます。

### 3D シェーディング属性

  * `shading = Makie.automatic` は使用される照明アルゴリズムを設定します。オプションは `NoShading`（照明なし）、`FastShading`（AmbientLight + PointLight）または `MultiLightShading`（複数の光、GLMakie のみ）です。これは RPRMakie には影響しないことに注意してください。
  * `diffuse::Vec3f = Vec3f(1.0)` は赤、緑、青のチャンネルが拡散（散乱）光にどの程度反応するかを設定します。
  * `specular::Vec3f = Vec3f(0.4)` はオブジェクトが赤、緑、青のチャンネルで光をどの程度反射するかを設定します。
  * `shininess::Real = 32.0` は反射の鋭さを設定します。
  * `backlight::Float32 = 0f0` は反転法線を持つ二次光計算の重みを設定します。
  * `ssao::Bool = false` はプロットが ssao（スクリーンスペース環境光遮蔽）でレンダリングされるかどうかを調整します。これは 3D プロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

### カラー属性

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis` は数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出すことができます。
  * `colorscale::Function = identity` カラー変換関数。任意の関数を指定できますが、`Colorbar` と一緒に使用する場合は `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` と一緒に使用するのが最適です。
  * `colorrange::Tuple{<:Real, <:Real}` は `colormap` の開始点と終了点を表す値を設定します。
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)` は `color = NaN` のための置き換え色を設定します。
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing` はカラーレンジ未満の任意の値のための色を設定します。
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing` はカラーレンジを超える任意の値のための色を設定します。
  * `alpha = 1.0` はカラーマップまたはカラー属性のアルファ値を設定します。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファが指定された場合、乗算されます。

### 一般的な属性

  * `visible::Bool = true` はプロットがレンダリングされるかどうかを設定します。
  * `overdraw::Bool = false` はプロットが他のプロットの上に描画されるかどうかを設定します。これは特に GL バックエンドで深度チェックを無視することを意味します。
  * `transparency::Bool = false` はプロットが透明性をどのように扱うかを調整します。GLMakie では `transparency = true` は順序に依存しない透明性を使用します。
  * `fxaa::Bool = true` はプロットが fxaa（アンチエイリアス）でレンダリングされるかどうかを調整します。
  * `inspectable::Bool = true` はこのプロットが `DataInspector` に表示されるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0` はすべての他の変換の後のプロットの深度値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1` です。これは GLMakie と WGLMakie のみに適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `model::Makie.Mat4f` はプロットのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行った調整を置き換えます。
  * `space::Symbol = :data` はボリュームプロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。
