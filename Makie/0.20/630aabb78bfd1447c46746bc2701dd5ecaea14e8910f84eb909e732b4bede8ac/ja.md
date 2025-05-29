```
datashader(points::AbstractVector{<: Point})
```

!!! warning
    この機能は、APIがまだ確定していないため、破壊的なリリースの外で変更される可能性があります。実装のバグに注意し、奇妙な動作に遭遇した場合は問題をオープンしてください。


ポイントは、反復とインデックス取得をサポートする任意の配列タイプであり、メモリマップされた配列も含まれます。x座標とy座標のために別々の配列があり、変換とコピーを避けたい場合は、次のようにすることを検討してください：

```Julia
using Makie.StructArrays
points = StructArray{Point2f}((x, y))
datashader(points)
```

ただし、xとyに高速な反復/インデックス取得が実装されていない場合、これが新しい配列にコピーするよりも遅くなる可能性があることに注意してください。

最高のパフォーマンスを得るために、`method=Makie.AggThreads()`を使用し、`julia -tauto`でjuliaを起動するか、環境変数`JULIA_NUM_THREADS`を持っているコアの数に設定してください。

## 属性

### `DataShader`に特有

  * `agg = AggCount()`は`AggCount()`、`AggAny()`または`AggMean()`にすることができます。ユーザーはオーバーロードによって拡張可能です：

````
```Julia
    struct MyAgg{T} <: Makie.AggOp end
    MyAgg() = MyAgg{Float64}()
    Makie.Aggregation.null(::MyAgg{T}) where {T} = zero(T)
    Makie.Aggregation.embed(::MyAgg{T}, x) where {T} = convert(T, x)
    Makie.Aggregation.merge(::MyAgg{T}, x::T, y::T) where {T} = x + y
    Makie.Aggregation.value(::MyAgg{T}, x::T) where {T} = x
```
````

  * `method = AggThreads()`は`AggThreads()`または`AggSerial()`にすることができます。
  * `async::Bool = true`は、タスク内でget_aggregationを計算し、忙しい間はズーム/パンの更新をスキップします。インタラクションに最適ですが、例えばpngに保存する場合やドキュメンターにインラインする場合は無効にする必要があります。
  * `operation::Function = automatic`は、表示前に全体のget*aggregation配列に対して呼び出される`Makie.equalize_histogram`関数にデフォルト設定されています（`operation(final*aggregation_result)`）。
  * `local_operation::Function = identity`は、集約後に各要素に対して呼び出される関数です（`map!(x-> local_operation(x), final_aggregation_result)`）。
  * `point_transform::Function = identity`は、集約する前に各ポイントに適用される関数です。
  * `binsize::Number = 1`は、1画面ピクセルあたりに希望するビンの数を定義する係数です。粗い画像を希望する場合はn > 1に設定します。
  * `show_timings::Bool = false`は、各フレームを集約するのにかかる時間を表示します。
  * `interpolate::Bool = true`は、結果の画像が補間されて表示されるべきかどうかを示します。

### 色属性

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis`は、数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。
  * `colorscale::Function = identity`は、色変換関数です。任意の関数を使用できますが、`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`および`Makie.Symlog10`と一緒に使用する場合にのみうまく機能します。
  * `colorrange::Tuple{<:Real, <:Real}`は、`colormap`の開始点と終了点を表す値を設定します。
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)`は、`color = NaN`のための置き換え色を設定します。
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing`は、カラーレンジ未満の任意の値のための色を設定します。
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing`は、カラーレンジを超える任意の値のための色を設定します。
  * `alpha = 1.0`は、カラーマップまたは色属性のアルファ値を設定します。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファがある場合、それらは乗算されます。

### 一般属性

  * `visible::Bool = true`は、プロットがレンダリングされるかどうかを設定します。
  * `overdraw::Bool = false`は、プロットが他のプロットの上に描画されるかどうかを設定します。これは特にGLバックエンドで深度チェックを無視することを意味します。
  * `transparency::Bool = false`は、プロットが透明性をどのように扱うかを調整します。GLMakieで`transparency = true`は、順序に依存しない透明性を使用する結果になります。
  * `fxaa::Bool = true`は、プロットがfxaa（アンチエイリアス）でレンダリングされるかどうかを調整します。
  * `inspectable::Bool = true`は、このプロットが`DataInspector`によって見えるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0`は、すべての他の変換後のプロットの深度値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1`です。これはGLMakieおよびWGLMakieにのみ適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `model::Makie.Mat4f`は、プロットのためのモデル行列を設定します。これは`translate!`、`rotate!`および`scale!`で行った調整を置き換えます。
  * `space::Symbol = :data`は、ボリュームプロットを包含するボックスの変換空間を設定します。可能な入力については`Makie.spaces()`を参照してください。
