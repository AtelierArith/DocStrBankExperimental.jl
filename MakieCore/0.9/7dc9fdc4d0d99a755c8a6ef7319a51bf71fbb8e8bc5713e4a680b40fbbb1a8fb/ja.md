```
arrows(points, directions; kwargs...)
arrows(x, y, u, v)
arrows(x::AbstractVector, y::AbstractVector, u::AbstractMatrix, v::AbstractMatrix)
arrows(x, y, z, u, v, w)
arrows(x, y, [z], f::Function)
```

指定された点に指定された成分で矢印をプロットします。`u` と `v` はベクトル成分として解釈され（`u` が x、`v` が y）、ベクトルは `x`、`y` で尾を持ってプロットされます。

`x, y, u, v` が `<: AbstractVector` の場合、各「行」は単一のベクトルとしてプロットされます。

`u, v` が `<: AbstractMatrix` の場合、`x` と `y` はグリッドの仕様として解釈され、`u, v` はグリッドに沿って矢印としてプロットされます。

`arrows` は三次元でも動作します。

`u, v, [w]` の代わりに `Function` が提供される場合、それは `Point` を入力として受け取り、適切な次元の `Point`、`Vec`、または他の配列のような出力を返す必要があります。

## プロットタイプ

`arrows` 関数のプロットタイプエイリアスは `Arrows` です。

## 属性

**`align`** =  `:origin`  — 矢印の位置を設定します。デフォルトでは、矢印は指定された位置から始まり、指定された方向に沿って伸びます。この属性が `:head`、`:lineend`、`:tailend`、`:headstart` または `:center` に設定されている場合、指定された位置は各矢印の頭と尾の間になります。

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファがある場合、掛け算されます。

**`arrowcolor`** =  `automatic`  — 矢印の頭の色を設定します。`automatic` に設定されている場合は `color` をコピーします。

**`arrowhead`** =  `automatic`  — 矢印の頭として使用されるマーカー（2D）またはメッシュ（3D）を定義します。2D のデフォルトは `'▲'` で、3D のデフォルトは円錐メッシュです。後者の場合、メッシュは `Point3f(0)` から始まり、正の z 方向を指す必要があります。

**`arrowsize`** =  `automatic`  — 矢印の頭のサイズをスケーリングします。2D の場合はデフォルトで `0.3`、3D の場合は `Vec3f(0.2, 0.2, 0.3)` です。後者の場合、最初の2つの成分は半径（x/y方向）をスケーリングし、最後の成分は円錐の長さをスケーリングします。`arrowsize` が 1 に設定されている場合、円錐の直径と長さは 1 になります。

**`arrowtail`** =  `automatic`  — 3D で矢印の尾を描画するために使用されるメッシュを定義します。`Point3f(0)` から始まり、負の z 方向に延びる必要があります。デフォルトは円柱です。これは 2D プロットには影響しません。

**`backlight`** =  `0.0`  — 反転法線を使用した二次光計算の重みを設定します。

**`clip_planes`** =  `automatic`  — クリップ平面は 3D 空間でクリッピングを行う方法を提供します。ここに最大 8 つの `Plane3f` 平面のベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]` を渡すことで親の `clip_planes` を削除できます。

**`color`** =  `:black`  — 矢印の頭と線の色を設定します。`linecolor` と `arrowcolor` を使用して別々にオーバーライドできます。

**`colormap`** =  `@inherit colormap :viridis`  — 数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap` の開始点と終了点を表す値です。

**`colorscale`** =  `identity`  — 色変換関数です。任意の関数を使用できますが、`Colorbar` と一緒に `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` と一緒にうまく機能します。

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深さ値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1` です。これは GLMakie と WGLMakie のみ適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。

**`diffuse`** =  `1.0`  — 赤、緑、青の各チャンネルが拡散（散乱）光にどれだけ反応するかを設定します。

**`fxaa`** =  `automatic`  — プロットが fxaa（アンチエイリアス、GLMakie のみ）でレンダリングされるかどうかを調整します。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色です。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector でカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspector によって生成されるデフォルトのラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`lengthscale`** =  `1.0`  — 矢印の尾の長さをスケーリングします。

**`linecolor`** =  `automatic`  — 2D で線として表される矢印の尾に使用される色を設定します。`automatic` に設定されている場合は `color` をコピーします。

**`linestyle`** =  `nothing`  — 2D で使用される線のスタイルを設定します。3D プロットには適用されません。

**`linewidth`** =  `automatic`  — 矢印の尾の幅/直径をスケーリングします。2D のデフォルトは `1`、3D のデフォルトは `0.05` です。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色です。

**`markerspace`** =  `:pixel`  — *ドキュメントは利用できません。*

**`material`** =  `nothing`  — 複雑な RadeonProRender 材料を設定するための RPRMakie のみの属性。         *警告*、RPR 材料の設定方法は変更される可能性があり、他のバックエンドはこの属性を無視します。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN 値の色です。

**`normalize`** =  `false`  — デフォルトでは、`arrows` に与えられた方向の長さが矢印の尾の長さをスケーリングするために使用されます。この属性が true に設定されている場合、方向は正規化され、このスケーリングはスキップされます。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特に GL バックエンドで深さチェックを無視することを意味します。

**`quality`** =  `32`  — 矢印の頭と尾のメッシュを生成する際に使用される角度の細分化数を定義します。パフォーマンスの問題がある場合は、これを下げることを検討してください。3D プロットにのみ適用されます。

**`shading`** =  `automatic`  — 使用される照明アルゴリズムを設定します。オプションは `NoShading`（照明なし）、`FastShading`（AmbientLight + PointLight）または `MultiLightShading`（複数の光、GLMakie のみ）です。これは RPRMakie には影響しないことに注意してください。

**`shininess`** =  `32.0`  — 反射がどれだけ鋭いかを設定します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`specular`** =  `0.2`  — オブジェクトが赤、緑、青の各チャンネルで光をどれだけ反射するかを設定します。

**`ssao`** =  `false`  — プロットが ssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは 3D プロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`transform_marker`** =  `automatic`  — マーカー属性がモデル行列によって変換されるかどうかを制御します。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakie では `transparency = true` は順序独立透明性を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
