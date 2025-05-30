```
meshscatter(positions)
meshscatter(x, y)
meshscatter(x, y, z)
```

`(x, y, z)`、`(x, y)`、または`positions`の各要素に対してメッシュをプロットします（`scatter`に似ています）。`markersize`は、`marker`として渡されたプリミティブに適用されるスケーリングです。

## プロットタイプ

`meshscatter`関数のプロットタイプエイリアスは`MeshScatter`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファは掛け算されます。

**`backlight`** =  `0.0`  — 反転法線を持つ二次光計算のための重みを設定します。

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`平面のベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`color`** =  `@inherit markercolor`  — マーカーの色を設定します。

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を指定できますが、`Colorbar`と一緒に使用する場合にのみ、`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`、`Makie.Symlog10`とよく機能します。

**`cycle`** =  `[:color]`  — *ドキュメントは利用できません。*

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。

**`diffuse`** =  `1.0`  — 赤、緑、青のチャンネルが拡散（散乱）光にどれだけ強く反応するかを設定します。

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス、GLMakieのみ）でレンダリングされるかどうかを調整します。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`によって表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`marker`** =  `:Sphere`  — 散乱メッシュを設定します。

**`markersize`** =  `0.1`  — メッシュのスケールを設定します。これは、各散乱メッシュに個別に適用するために`Vector`として指定できます。

**`material`** =  `nothing`  — 複雑なRadeonProRenderマテリアルを設定するためのRPRMakie専用属性。 *警告*、RPRマテリアルの設定方法は変更される可能性があり、他のバックエンドはこの属性を無視します。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは、`translate!`、`rotate!`、および`scale!`で行った調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`rotation`** =  `0.0`  — メッシュの回転を設定します。数値の回転はz軸の周りで、`Vec3f`はメッシュが回転するようにし、z軸がそのベクトルになります。クォータニオンは一般的な回転を記述します。これは、各散乱メッシュに個別に適用するためにベクトルとして指定できます。

**`shading`** =  `automatic`  — 使用される照明アルゴリズムを設定します。オプションは`NoShading`（照明なし）、`FastShading`（AmbientLight + PointLight）、または`MultiLightShading`（複数の光、GLMakieのみ）です。これはRPRMakieには影響しないことに注意してください。

**`shininess`** =  `32.0`  — 反射の鋭さを設定します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`specular`** =  `0.2`  — オブジェクトが赤、緑、青のチャンネルで光をどれだけ強く反射するかを設定します。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`のときにのみ適用されます。

**`transform_marker`** =  `true`  — （完全な）モデル行列が散乱メッシュに適用されるかどうかを制御します。これがfalseの場合、`scale!`、`rotate!`、および`translate!()`は散乱メッシュに影響を与えません。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序独立透明性を使用する結果になります。

**`uv_transform`** =  `automatic`  — 散乱メッシュにテクスチャがどのようにマッピングされるかを制御するuv座標の変換を設定します。メッシュにはこれに必要なuv座標が含まれている必要がありますが、これはデフォルトでは幾何学的プリミティブには含まれていません。例えば、`prim = Rect2f(0, 0, 1, 1)`を使用して`GeometryBasics.uv_normal_mesh(prim)`を使用できます。この属性は`I`、`scale::VecTypes{2}`、`(translation::VecTypes{2}, scale::VecTypes{2})`、`:rotr90`、`:rotl90`、`:rot180`、`:swap*xy/:transpose`、`:flip*x`、`:flip*y`、`:flip*xy`、または一般的には`Makie.Mat{2, 3, Float32}`または`Makie.Mat3f`として`Makie.uv_transform()`によって返されるものに設定できます。また、上記のいずれかを渡すことで散乱メッシュごとに設定でき、操作はタプル`(op3, op2, op1)`を渡すことで変更できます。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
