```
arc(origin, radius, start_angle, stop_angle; kwargs...)
```

この関数は、`origin`を中心とし、半径`radius`の円弧を、`start_angle`から`stop_angle`までプロットします。`origin`は2次元の座標（すなわち`Point2`）でなければならず、他の引数はすべて`<: Number`でなければなりません。

例:

`arc(Point2f(0), 1, 0.0, π)` `arc(Point2f(1, 2), 0.3, π, -π)`

## プロットタイプ

`arc`関数のプロットタイプエイリアスは`Arc`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファがある場合、掛け算されます。

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`平面のベクトルを設定でき、その後ろでプロットがクリップされます（すなわち、見えなくなります）。デフォルトでは、クリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`color`** =  `@inherit linecolor`  — 線の色。

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを見るには、`Makie.available_gradients()`を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar`と一緒に使用する場合は`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`および`Makie.Symlog10`と一緒にうまく機能します。

**`cycle`** =  `[:color]`  — 複数のプロットを作成する際にサイクルする属性を設定します。

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深さ値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `false`  — プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakieのみ）。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`で表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`joinstyle`** =  `@inherit joinstyle`  — コーナーでのレンダリングを制御します。オプションは、鋭いコーナーのための`:miter`、"切り取られた"コーナーのための`:bevel`、および丸みを帯びたコーナーのための`:round`です。コーナー角が`miter_limit`未満の場合、`:miter`は長いスパイクを避けるために`:bevel`と同等です。

**`linecap`** =  `@inherit linecap`  — 使用されるラインキャップのタイプを設定します。オプションは、`:butt`（押し出しなしの平坦）、`:square`（半分のライン幅の押し出しを持つ平坦）、または`:round`です。

**`linestyle`** =  `nothing`  — 線のダッシュパターンを設定します。オプションは、`:solid`（`nothing`に相当）、`:dot`、`:dash`、`:dashdot`および`:dashdotdot`です。これらは、ギャップスタイル修飾子`(:normal, :dense, :loose)`を持つタプルでも指定できます。例えば、`(:dot, :loose)`または`(:dashdot, :dense)`のように。

カスタムパターンについては、[`Makie.Linestyle`](@ref)を参照してください。

**`linewidth`** =  `@inherit linewidth`  — スクリーン単位での線の幅を設定します。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`miter_limit`** =  `@inherit miter_limit`  — ミタージョインが切り捨てられる最小内角を設定します。`Makie.miter_distance_to_angle`も参照してください。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは、`translate!`、`rotate!`および`scale!`で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深さチェックを無視することを意味します。

**`resolution`** =  `361`  — 円弧を近似する線のポイント数。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`のときにのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは、`transparency = true`は順序に依存しない透明性を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。 ```
