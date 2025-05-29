```
Periodic{P, S}(f, period::P, [phase_shift::S]) <: Transform
```

提供された `period` と `phase_shift` を用いて、データに周期関数 `f` を適用します。

`period` と `phase_shift` は、データが `Real` または `TimeType` のいずれかに応じて、同じスーパタイプの `Real` または `Period` を持たなければなりません。

!!! note
    `TimeType` データの場合、同じ時間量が記述されていても、与えられた `period` のタイプによって結果が変わります。例: `Week(1)` と `Second(Week(1))`；前者は最も最近の月曜日に期間を開始しますが、後者は時間 0 から604800秒の最近の倍数に期間を開始します。


# フィールド

  * `f::Union{typeof(cos), typeof(sin)}`: 周期関数
  * `period::Union{Real, Period}`: 関数の周期。厳密に正でなければなりません。
  * `phase_shift::Union{Real, Period}` (オプション): 周期関数の位相を調整します。入力と同じ単位で測定されます。値を増加させると、関数が右に移動し、高い/遅い入力値に向かいます。
