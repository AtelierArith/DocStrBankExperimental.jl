```
datashader(points::AbstractVector{<: Point})
```

!!! warning
    この機能は、APIがまだ確定していないため、破壊的リリースの外で変更される可能性があります。実装のバグに注意し、奇妙な動作に遭遇した場合は問題をオープンしてください。


ポイントは、反復とインデックス取得をサポートする任意の配列タイプであり、メモリマップされた配列も含まれます。x座標とy座標の別々の配列があり、変換とコピーを避けたい場合は、次のように使用することを検討してください：

```Julia
using Makie.StructArrays
points = StructArray{Point2f}((x, y))
datashader(points)
```

ただし、xとyに高速な反復/インデックス取得が実装されていない場合、データを新しい配列にコピーするよりも遅くなる可能性があることに注意してください。

最高のパフォーマンスを得るために、`method=Makie.AggThreads()`を使用し、`julia -tauto`でjuliaを起動するか、`JULIA_NUM_THREADS`環境変数を持っていることを確認してください。

## プロットタイプ

`datashader`関数のプロットタイプエイリアスは`DataShader`です。

## 属性

**`agg`** =  `AggCount{Float32}()`  — `AggCount()`, `AggAny()`または`AggMean()`である可能性があります。正しい要素タイプ、例えば`AggCount{Float32}()`を使用することを確認してください。これは`local_operation`の出力を収容する必要があります。オーバーロードによってユーザー拡張可能です：

```julia
struct MyAgg{T} <: Makie.AggOp end
MyAgg() = MyAgg{Float64}()
Makie.Aggregation.null(::MyAgg{T}) where {T} = zero(T)
Makie.Aggregation.embed(::MyAgg{T}, x) where {T} = convert(T, x)
Makie.Aggregation.merge(::MyAgg{T}, x::T, y::T) where {T} = x + y
Makie.Aggregation.value(::MyAgg{T}, x::T) where {T} = x
```

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファは掛け算されます。

**`async`** =  `true`  — `get_aggregation`をタスクで計算し、忙しい間はズーム/パンの更新をスキップします。インタラクションに最適ですが、例えばpngに保存する場合やDocumenterにインラインする場合は無効にする必要があります。

**`binsize`** =  `1`  — 画面のピクセルごとにいくつのビンを希望するかを定義するファクター。粗い画像を希望する場合はn > 1に設定します。

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でのクリッピングを行う方法を提供します。ここに最大8つの`Plane3f`平面のベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトでは、クリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]`を渡すことで親の`clip_planes`を削除できます。

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar`と一緒に`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`および`Makie.Symlog10`と一緒にうまく機能します。

**`depth_shift`** =  `0.0`  — すべての他の変換の後にプロットの深度値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1`の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。

**`fxaa`** =  `true`  — プロットがfxaa（アンチエイリアス、GLMakieのみ）でレンダリングされるかどうかを調整します。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが`DataInspector`によって表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector内のカスタムインジケーターをクリーンアップするためのコールバック関数`(inspector, plot) -> ...`を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの`show_data`メソッドを置き換えるコールバック関数`(inspector, plot, index) -> ...`を設定します。

**`inspector_label`** =  `automatic`  — DataInspectorによって生成されるデフォルトのラベルを置き換えるコールバック関数`(plot, index, position) -> string`を設定します。

**`interpolate`** =  `false`  — 結果の画像が補間表示されるべきかどうか。補間は、いくつかのバックエンドでNaNに隣接するビンもNaNにする可能性があることに注意してください。これは、GPUハードウェアで使用される補間スキームによるものです。これにより、実際よりも多くのNaNビンが存在するように見えることがあります。

**`local_operation`** =  `identity`  — 集約後に各要素に対して呼び出される関数（`map!(x-> local_operation(x), final_aggregation_result)`）。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`method`** =  `AggThreads()`  — スレッド化された集約のための`AggThreads()`またはシリアル集約のための`AggSerial()`である可能性があります。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは、`translate!`、`rotate!`および`scale!`で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN値の色。

**`operation`** =  `automatic`  — 表示前に全体のget*aggregation配列に対して呼び出される`Makie.equalize_histogram`関数にデフォルト設定されます（`operation(final*aggregation_result)`）。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特にGLバックエンドでの深度チェックを無視することを意味します。

**`point_transform`** =  `identity`  — 集約する前に各ポイントに適用される関数。

**`show_timings`** =  `false`  — 各フレームを集約するのにかかる時間を表示するには`true`に設定します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。

**`ssao`** =  `false`  — プロットがssao（スクリーンスペース環境光遮蔽）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true`のときにのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakieでは`transparency = true`は順序独立透明性を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
