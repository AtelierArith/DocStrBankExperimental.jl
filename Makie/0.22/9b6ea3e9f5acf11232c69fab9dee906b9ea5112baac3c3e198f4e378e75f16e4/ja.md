```
band(x, ylower, yupper; kwargs...)
band(lower, upper; kwargs...)
band(x, lowerupper; kwargs...)
```

`ylower` から `yupper` までのバンドを `x` に沿ってプロットします。`band(lower, upper)` の形式は、`lower` と `upper` の点の間に [ルールドサーフェス](https://en.wikipedia.org/wiki/Ruled_surface) をプロットします。両方の境界は、区間のベクトルである `lowerupper` として一緒に渡すことができます。

## プロットタイプ

`band` 関数のプロットタイプエイリアスは `Band` です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファが掛け合わされます。

**`backlight`** =  `0.0`  — 反転法線を持つ二次光計算の重みを設定します。

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの `Plane3f` 平面のベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]` を渡すことで親の `clip_planes` を削除できます。

**`color`** =  `@inherit patchcolor`  — メッシュの色を設定します。頂点ごとの色のための `Vector{<:Colorant}` または単一の `Colorant` であることができます。テクスチャを使用してメッシュに色を付けるために `Matrix{<:Colorant}` を使用することができ、これにはメッシュがテクスチャ座標を含む必要があります。`<: AbstractPattern` を使用して、メッシュに繰り返しのピクセルサンプリングパターンを適用できます（例：ハッチング用）。

**`colormap`** =  `@inherit colormap :viridis`  — 数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap` の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar` と一緒に `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` と一緒にうまく機能します。

**`cycle`** =  `[:color => :patchcolor]`  — *ドキュメントは利用できません。*

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1` の範囲です。これは GLMakie と WGLMakie のみに適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。

**`diffuse`** =  `1.0`  — 赤、緑、青のチャンネルが拡散（散乱）光にどれだけ強く反応するかを設定します。

**`direction`** =  `:x`  — バンドの方向。`:y` に設定すると、x および y 座標が反転し、垂直バンドになります。この設定は2Dバンドにのみ適用されます。

**`fxaa`** =  `true`  — プロットが fxaa（アンチエイリアス、GLMakie のみ）でレンダリングされるかどうかを調整します。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector でカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspector によって生成されるデフォルトラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`interpolate`** =  `true`  — 色が補間されるべきかどうかを設定します。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`matcap`** =  `nothing`  — *ドキュメントは利用できません。*

**`material`** =  `nothing`  — 複雑な RadeonProRender 材料を設定するための RPRMakie のみの属性。         *警告*、RPR 材料の設定方法は変更される可能性があり、他のバックエンドはこの属性を無視します。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行った調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN 値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特に GL バックエンドで深度チェックを無視することを意味します。

**`shading`** =  `NoShading`  — 使用される照明アルゴリズムを設定します。オプションは `NoShading`（照明なし）、`FastShading`（AmbientLight + PointLight）または `MultiLightShading`（複数の光、GLMakie のみ）です。これは RPRMakie には影響しないことに注意してください。

**`shininess`** =  `32.0`  — 反射の鋭さを設定します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`specular`** =  `0.2`  — オブジェクトが赤、緑、青のチャンネルで光をどれだけ強く反射するかを設定します。

**`ssao`** =  `false`  — プロットが ssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakie では `transparency = true` は順序独立透明性を使用する結果になります。

**`uv_transform`** =  `automatic`  — テクスチャがメッシュにどのようにマッピングされるかを制御する uv 座標の変換を設定します。この属性は `I`、`scale::VecTypes{2}`、`(translation::VecTypes{2}, scale::VecTypes{2})`、`:rotr90`、`:rotl90`、`:rot180`、`:swap*xy/:transpose`、`:flip*x`、`:flip*y`、`:flip*xy`、または一般的には `Makie.Mat{2, 3, Float32}` または `Makie.Mat3f`（`Makie.uv_transform()` によって返される）を使用できます。これらはタプル `(op3, op2, op1)` を渡すことで変更することもできます。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
