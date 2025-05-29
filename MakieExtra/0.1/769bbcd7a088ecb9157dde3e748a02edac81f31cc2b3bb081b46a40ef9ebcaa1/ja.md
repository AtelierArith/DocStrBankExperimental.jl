```
arrowlines(positions; arrowstyle="-|>", ...)
```

`lines()`と同様ですが、線の一方または両方の端に矢印があります。すべての`lines()`および`scatter()`属性をサポートしています。

`arrowstyle`属性を追加します。これは次の形式の文字列です：`<left marker><line style><right marker>` ここで、`<left marker>`および`<right marker>`は`"", "<", "<|", ">", "|>"`のいずれかであり、`<line style>`は`"-", "--", ".."`のいずれかです。

## プロットタイプ

`arrowlines`関数のプロットタイプエイリアスは`ArrowLines`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファがある場合、掛け算されます。

**`arrowstyle`** =  `"-|>"`  — *ドキュメントは利用できません。*

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`平面のベクトルを設定でき、その後ろのプロットはクリップされます（つまり、見えなくなります）。デフォルトでは、クリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`color`** =  `@inherit linecolor`  — 線の色。

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を指定できますが、`Colorbar`と一緒に使用する場合は`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`および`Makie.Symlog10`と一緒にうまく機能します。

**`cycle`** =  `[:color]`  — 複数のプロットを作成する際にサイクルする属性を設定します。

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`depthsorting`** =  `false`  — マーカーの深度ソートを有効にし、境界アーティファクトを改善できます。現在、GLMakieでのみサポートされています。

**`distancefield`** =  `nothing`  — フォントやベジエパスのレンダリングなどに使用されるオプションの距離フィールド。自動的に設定されます。

**`font`** =  `@inherit markerfont`  — キャラクターマーカーに使用されるフォントを設定します。フォントの（部分的な）名前やフォントファイルのファイルパスを指定する`String`であることができます。

**`fxaa`** =  `false`  — プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakieのみ）。

**`glowcolor`** =  `(:black, 0.0)`  — マーカーの周りのグロー効果の色を設定します。

**`glowwidth`** =  `0.0`  — マーカーの周りのグロー効果のサイズを設定します。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`で表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`joinstyle`** =  `@inherit joinstyle`  — コーナーでのレンダリングを制御します。オプションは、鋭いコーナーのための`:miter`、"切り取られた"コーナーのための`:bevel`、丸みを帯びたコーナーのための`:round`です。コーナー角度が`miter_limit`未満の場合、`:miter`は長いスパイクを避けるために`:bevel`と同等です。

**`linecap`** =  `@inherit linecap`  — 使用されるラインキャップのタイプを設定します。オプションは、`:butt`（押し出しなしのフラット）、`:square`（半分のライン幅の押し出しを持つフラット）、または`:round`です。

**`linestyle`** =  `nothing`  — 線のダッシュパターンを設定します。オプションは、`:solid`（`nothing`と同等）、`:dot`、`:dash`、`:dashdot`および`:dashdotdot`です。これらは、ギャップスタイル修飾子`(:normal, :dense, :loose)`を持つタプルでも指定できます。例えば、`(:dot, :loose)`や`(:dashdot, :dense)`です。

カスタムパターンについては、[`Makie.Linestyle`](@ref)を参照してください。

**`linewidth`** =  `@inherit linewidth`  — スクリーン単位での線の幅を設定します。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`marker`** =  `@inherit marker`  — スキャターマーカーを設定します。

**`marker_offset`** =  `Vec3f(0)`  — `markerspace`単位での指定位置からのマーカーのオフセット。オフセットが0の場合、マーカーは中央に配置されます。

**`markersize`** =  `@inherit markersize`  — 各マーカーの基準サイズに対してスケーリングすることによってマーカーのサイズを設定します。`Real`はxおよびyの次元を同じ量だけスケーリングします。2つの要素を持つ`Vec`または`Tuple`はxとyを別々にスケーリングします。いずれかの配列は各マーカーを別々にスケーリングします。人間はマーカーの面積をそのサイズとして認識し、`markersize`が二次的に増加するため、`markersize`を2倍にすると、視覚的に4倍の大きさのマーカーになります。

**`markerspace`** =  `:pixel`  — `markersize`が指定される空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`miter_limit`** =  `@inherit miter_limit`  — ミタージョインが切り捨てられる最小内角を設定します。`Makie.miter_distance_to_angle`も参照してください。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは`translate!`、`rotate!`および`scale!`で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`rotation`** =  `Billboard()`  — マーカーの回転を設定します。`Billboard`の回転は常に深度軸の周りです。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`と一緒にのみ適用されます。

**`strokecolor`** =  `@inherit markerstrokecolor`  — マーカーの周りのアウトラインの色を設定します。

**`strokewidth`** =  `@inherit markerstrokewidth`  — マーカーの周りのアウトラインの幅を設定します。

**`transform_marker`** =  `false`  — モデル行列（平行移動なし）がマーカー自体に適用されるかどうかを制御します。これが真の場合、`scale!`および`rotate!`はマーカーに影響を与えます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは、`transparency = true`は順序に依存しない透明性を使用します。

**`uv_offset_width`** =  `(0.0, 0.0, 0.0, 0.0)`  — *ドキュメントは利用できません。*

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
