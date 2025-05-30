```
spy(z::AbstractSparseArray)
spy(x_range::NTuple{2, Number}, y_range::NTuple{2, Number}, z::AbstractSparseArray)
spy(x_range::ClosedInterval, y_range::ClosedInterval, z::AbstractSparseArray)
```

大きな疎行列を視覚化します。使用法：

```julia
using SparseArrays, GLMakie
N = 200_000
x = sprand(Float64, N, N, (3(10^6)) / (N*N));
spy(x)
# または、xとyの範囲を指定したい場合：
spy(0..1, 0..1, x)
```

## プロットタイプ

`spy`関数のプロットタイプエイリアスは`Spy`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファが掛け合わされます。

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`平面のベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトではクリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`color`** =  `nothing`  — デフォルトではマーカーの色は行列内の値によって決定されますが、`color`を介して上書きできます。

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラースケールを確認するには、`Makie.available_gradients()`を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar`と一緒に使用する場合は`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`および`Makie.Symlog10`と一緒にうまく機能します。

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。つまり、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。

**`framecolor`** =  `:black`  — デフォルトではデータの周りにフレームが描画され、`framecolor`属性がその色に使用されます。

**`framesize`** =  `1`  — フレームのライン幅

**`framevisible`** =  `true`  — フレームを描画するかどうか。

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します（GLMakieのみ）。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`で表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`marker`** =  `Rect`  — `scatter!`でサポートされている任意のマーカーを使用できます。巨大な疎配列の場合は、非常に高速ですが、正方形のマーカーしかレンダリングできない`FastPixel`を使用する必要があります。したがって、`Axis(...; aspect=1)`なしでは、マーカーのサイズが正しくありません。比較：

```julia
data = sprand(10, 10, 0.5)
f = Figure()
spy(f[1, 1], data; marker=FastPixel())
spy(f[1, 2], data; marker=FastPixel(), axis=(; aspect=1))
f
```

**`marker_gap`** =  `0`  — マーカーのサイズを小さくして、マーカー間に隙間を作ります。これの単位はデータ空間です。

**`markersize`** =  `automatic`  — markersize=automaticは、マーカーのサイズをデータに合わせますが、手動で設定することもできます。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは`translate!`、`rotate!`および`scale!`で行った調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドで深度チェックを無視することを意味します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境光遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`と一緒にのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序に依存しない透明性を使用します。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
