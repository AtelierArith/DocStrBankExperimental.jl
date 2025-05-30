```
voxels(x, y, z, chunk::Array{<:Real, 3})
voxels(chunk::Array{<:Real, 3})
```

0を中心としたボクセルのチャンクをプロットします。オプションで、チャンクの配置とスケーリングを範囲のようにx、y、zで指定できます。（ここでは端点のみが考慮されます。ボクセルは常に均一なサイズです。）

内部的にはボクセルは8ビットの符号なし整数として表現され、`0x00`は常に見えない「空気」ボクセルです。一致する型のチャンクを渡すと、これらの値が直接設定されます。色の処理は内部表現に特化しており、通常とは少し異なる動作をする場合があります。

`voxels`は現在実験的と見なされており、パッチリリースで破壊的変更が行われる可能性があります。

## プロットタイプ

`voxels`関数のプロットタイプエイリアスは`Voxels`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファが掛け合わされます。

**`backlight`** =  `0.0`  — 反転法線を持つ二次光計算の重みを設定します。

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でのクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`平面のベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトではクリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`color`** =  `nothing`  — ボクセルIDごとに色を設定し、`0x00`をスキップします。これは、IDが1のボクセルが`plot.colors[1]`を取得し、IDが255まで続くことを意味します。これは、テクスチャマッピング用の画像である色のマトリックスに設定することもできます。

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar`と一緒に`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`、`Makie.Symlog10`と一緒にうまく機能します。

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieとWGLMakieにのみ適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。

**`depthsorting`** =  `false`  — ボクセルのレンダリング順序を制御します。`false`に設定すると、視聴者に近いボクセルが最初にレンダリングされ、オーバードローが減少し、パフォーマンスが向上します。`true`に設定すると、ボクセルが前から後ろにレンダリングされ、透明なボクセルの正しい順序が有効になります。

**`diffuse`** =  `1.0`  — 赤、緑、青のチャンネルが拡散（散乱）光にどれだけ強く反応するかを設定します。

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス、GLMakieのみ）でレンダリングされるかどうかを調整します。

**`gap`** =  `0.0`  — ボクセルサイズの単位で隣接するボクセル間のギャップを設定します。これは0.01より大きくする必要があります。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`で表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`interpolate`** =  `false`  — テクスチャマップが補間（すなわち滑らかに）でサンプリングされるかどうかを制御します（すなわち、ピクセル化されるかどうか）。

**`is_air`** =  `x->begin         #= /Users/atelierarith/.julia/packages/MakieCore/G1QFL/src/basic_plots.jl:626 =#         isnothing(x) || (ismissing(x) || isnan(x))     end`  — 入力データ内のどの値が見えない（空気）ボクセルにマッピングされるかを制御する関数。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`material`** =  `nothing`  — RPRMakie専用の属性で、複雑なRadeonProRenderマテリアルを設定します。         *警告*、RPRマテリアルの設定方法は変更される可能性があり、他のバックエンドはこの属性を無視します。

**`model`** =  `automatic`  — プロットのモデルマトリックスを設定します。これは`translate!`、`rotate!`、`scale!`で行った調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`shading`** =  `automatic`  — 使用される照明アルゴリズムを設定します。オプションは`NoShading`（照明なし）、`FastShading`（AmbientLight + PointLight）または`MultiLightShading`（複数の光、GLMakieのみ）です。これはRPRMakieには影響しません。

**`shininess`** =  `32.0`  — 反射がどれだけ鋭いかを設定します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`specular`** =  `0.2`  — オブジェクトが赤、緑、青のチャンネルで光をどれだけ強く反射するかを設定します。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`のときにのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序独立透明性を使用します。

**`uv_transform`** =  `nothing`  — テクスチャマッピングを使用するには、`uv_transform`を定義する必要があり、`color`は画像である必要があります。`uv_transform`は、各インデックスが`UInt8`ボクセルID（0をスキップ）にマッピングされる`Vector`として指定するか、2番目のインデックスが`(-x, -y, -z, +x, +y, +z)`の順序に従って側面にマッピングされる`Matrix`として指定できます。各要素は`Vec3f(uv, 1)`に適用される`Mat{2, 3, Float32}`として機能し、uvは各ボクセルのために0..1の範囲で生成されます。結果はテクスチャをサンプリングするために使用されます。UV変換には、例えば`(Point2f(x, y), Vec2f(xscale, yscale))`のように使用できる多くのショートハンドがあります。これらは`?Makie.uv_transform`にリストされています。

**`uvmap`** =  `nothing`  — 非推奨 - uv_transformを使用してください。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
