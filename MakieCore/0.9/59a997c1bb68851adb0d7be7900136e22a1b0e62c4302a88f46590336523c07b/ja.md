```
scatter(positions)
scatter(x, y)
scatter(x, y, z)
```

`(x, y, z)`, `(x, y)`、または `positions` の各要素に対してマーカーをプロットします。

## プロットタイプ

`scatter` 関数のプロットタイプエイリアスは `Scatter` です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファがある場合、掛け算されます。

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの `Plane3f` 平面のベクターを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]` を渡すことで親の `clip_planes` を削除できます。

**`color`** =  `@inherit markercolor`  — マーカーの色を設定します。色が設定されていない場合、`scatter!` の複数の呼び出しは軸のカラーパレットを循環します。

**`colormap`** =  `@inherit colormap :viridis`  — 数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラグラデーションを確認するには、`Makie.available_gradients()` を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap` の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — カラー変換関数。任意の関数を指定できますが、`Colorbar` と一緒に使用する場合は `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` と一緒にうまく機能します。

**`cycle`** =  `[:color]`  — 複数のプロットを作成する際に循環させる属性を設定します。

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1` の範囲です。これは GLMakie と WGLMakie のみに適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。

**`depthsorting`** =  `false`  — マーカーの深度ソートを有効にし、ボーダーアーティファクトを改善できます。現在は GLMakie のみでサポートされています。

**`distancefield`** =  `nothing`  — フォントやベジエパスのレンダリングに使用されるオプションの距離フィールド。自動的に設定されます。

**`font`** =  `@inherit markerfont`  — キャラクターマーカーに使用されるフォントを設定します。フォントの（部分的な）名前やフォントファイルのファイルパスを指定する `String` であることができます。

**`fxaa`** =  `false`  — プロットが fxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakie のみ）。

**`glowcolor`** =  `(:black, 0.0)`  — マーカーの周りのグロー効果の色を設定します。

**`glowwidth`** =  `0.0`  — マーカーの周りのグロー効果のサイズを設定します。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector でカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspector によって生成されるデフォルトのラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`marker`** =  `@inherit marker`  — スキャターマーカーを設定します。

**`marker_offset`** =  `Vec3f(0)`  — `markerspace` 単位で指定された位置からのマーカーのオフセット。オフセットが0の場合、マーカーは中央に配置されます。

**`markersize`** =  `@inherit markersize`  — 各マーカーの基準サイズに対して相対的にスケーリングすることによってマーカーのサイズを設定します。`Real` は x および y 次元を同じ量だけスケーリングします。2つの要素を持つ `Vec` または `Tuple` は x および y を別々にスケーリングします。いずれかの配列は各マーカーを別々にスケーリングします。人間はマーカーの面積をそのサイズとして認識し、`markersize` が二次的に増加するため、`markersize` を2倍にすると、視覚的には4倍の大きさのマーカーになります。

**`markerspace`** =  `:pixel`  — `markersize` が与えられる空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN 値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特に GL バックエンドで深度チェックを無視することを意味します。

**`rotation`** =  `Billboard()`  — マーカーの回転を設定します。`Billboard` 回転は常に深度軸の周りで行われます。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`ssao`** =  `false`  — プロットが ssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`strokecolor`** =  `@inherit markerstrokecolor`  — マーカーの周りのアウトラインの色を設定します。

**`strokewidth`** =  `@inherit markerstrokewidth`  — マーカーの周りのアウトラインの幅を設定します。

**`transform_marker`** =  `false`  — モデル行列（平行移動なし）がマーカー自体に適用されるかどうかを制御します。これは位置に対してのみ適用されます。（これが真の場合、`scale!` と `rotate!` はマーカーに影響を与えます。）

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakie では `transparency = true` は順序に依存しない透明性を使用します。

**`uv_offset_width`** =  `(0.0, 0.0, 0.0, 0.0)`  — *ドキュメントは利用できません。*

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
