```
hlines(ys; xmin = 0.0, xmax = 1.0, attrs...)
```

2Dプロジェクションを持つ`Scene`に横線を作成します。線はデータ座標の`ys`に配置され、シーン座標の`xmin`から`xmax`（0から1）まで描画されます。これらの3つはすべて単一または複数の値を持つことができ、最終的な線分を計算するためにブロードキャストされます。

## プロットタイプ

`hlines`関数のプロットタイプエイリアスは`HLines`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファが掛け合わされます。

**`clip_planes`** =  `automatic`  — クリッププレーンは3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`プレーンのベクトルを設定でき、その後ろのプロットはクリップされます（つまり、見えなくなります）。デフォルトでは、クリッププレーンは親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`color`** =  `@inherit linecolor`  — 線の色。

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar`と一緒に使用する場合は`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`および`Makie.Symlog10`と一緒にうまく機能します。

**`cycle`** =  `[:color]`  — 複数のプロットを作成する際にサイクルする属性を設定します。

**`depth_shift`** =  `0.0`  — すべての他の変換後にプロットの深度値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `false`  — プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakieのみ）。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`によって表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`linecap`** =  `@inherit linecap`  — 使用されるラインキャップのタイプを設定します。すなわち、:butt（押し出しのないフラット）、:square（1ライン幅の押し出しのあるフラット）または:round。

**`linestyle`** =  `nothing`  — 線のダッシュパターンを設定します。オプションは`:solid`（`nothing`に相当）、`:dot`、`:dash`、`:dashdot`および`:dashdotdot`です。これらはギャップスタイル修飾子とともにタプルで指定することもできます。修飾子は`:normal`、`:dense`または`:loose`です。例えば、`(:dot, :loose)`または`(:dashdot, :dense)`のように。

カスタムパターンについては、[`Makie.Linestyle`](@ref)を参照してください。

**`linewidth`** =  `@inherit linewidth`  — ピクセル単位での線の幅を設定します。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは`translate!`、`rotate!`および`scale!`で行った調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境光遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`のときにのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序に依存しない透明性を使用します。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。

**`xmax`** =  `1`  — x次元に沿った相対軸単位での線の終わり。

**`xmin`** =  `0`  — x次元に沿った相対軸単位での線の始まり。
