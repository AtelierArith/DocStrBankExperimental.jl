```
struct SegmentedTimeSpan
```

不変の構造体で、等しい長さの単位である*セグメント*に分割された長い時間範囲を表します。この構造体は通常、[`genpointings!`](@ref)および[`genpointings`](@ref)への連続的な呼び出しを行うために使用されます。

フィールドは以下の通りです：

  * `start_time` は時間範囲内の最初のサンプルの時間です
  * `sampling_time` は1つのサンプルのための統合時間です
  * `segment_duration` は1つのセグメントの持続時間です
  * `num_of_segments` は時間範囲内のセグメントの数です

以下の例は、1日ごとに持続する複数の範囲の合成として1年の時間範囲を定義します：

```julia
sts = SegmentedTimeSpan(
    start_time = 0.0,
    sampling_time = 0.1,
    segment_duration = 24 * 3600,
    num_of_segments = 365,
)
```

`SegmentedTimeSpan`が構築されると、それは`StepRangeLen`型の時間範囲の要素を持つ配列のように振る舞います。これを反復処理して、[`genpointings`](@ref)のような関数を実行できます：

```julia
for cur_time_span in sts
    pointings = genpointings(PICO_SCANNING_STRATEGY, cur_time_span, ...)

    # "pointings" には時間範囲のためのポイントが含まれています
end
```
