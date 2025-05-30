```
SegmentedWindowConfig <: IndicatorsChangeConfig
SegmentedWindowConfig(indicators, change_metrics, tseg_start, tseg_end; kwargs...)
```

[`estimate_changes`](@ref) に与えることができる設定です。ユーザー定義のウィンドウセグメント内で指標と変化を推定することによって遷移を推定します。以下のように行います：

1. 指定された各セグメントについて、入力時系列に対してウィンドウをスライドさせることによって対応する指標の時系列を推定します（ウィンドウセグメント内）。
2. 指標の時系列の各セグメントについて、指標の時系列の全セグメントに対して変化メトリックを適用することによってスカラー変化メトリックを推定します。

`tseg_start, tseg_end` はウィンドウセグメントの開始と終了です（ウィンドウセグメントは重複しても問題ありません）。`indicators, change_metrics` は [`SlidingWindowConfig`](@ref) と同じです。

`SlidingWindowConfig` に対応する結果出力は [`SegmentedWindowResults`](@ref) です。

## キーワード引数

  * `width_ind::Int=100, stride_ind::Int=1, whichtime = midpoint, T = Float64`：[`SlidingWindowConfig`](@ref) と同じキーワードです。
  * `min_width_cha::Int=typemax(Int)`：変化メトリックの推定を行うために必要な最小幅です。セグメントが十分に長くない場合、変化メトリックは `NaN` になります。
