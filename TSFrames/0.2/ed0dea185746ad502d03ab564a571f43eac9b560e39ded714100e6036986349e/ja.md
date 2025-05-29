### 周期変換

`TimeType` インデックス型の周波数変換のための便利なメソッドのセット。内部的には、実際の変換を行うために `endpoints()` を呼び出します。`n` は `period` 型の期間の数です。例えば、`to_monthly(tsf, 2)` は時系列を「2ヶ月ごと」にリサンプリングします。

```julia
to_period(tsf::TSFrame, period::T)::TSFrame where {T<:Period}
to_yearly(tsf::TSFrame, n=1)::TSFrame
to_quarterly(tsf::TSFrame, n=1)::TSFrame
to_monthly(tsf::TSFrame, n=1)::TSFrame
to_weekly(tsf::TSFrame, n=1)::TSFrame
to_daily(tsf::TSFrame, n=1)::TSFrame
to_hourly(tsf::TSFrame, n=1)::TSFrame
to_minutes(tsf::TSFrame, n=1)::TSFrame
to_seconds(tsf::TSFrame, n=1)::TSFrame
to_milliseconds(tsf::TSFrame, n=1)::TSFrame
to_microseconds(tsf::TSFrame, n=1)::TSFrame
to_nanoseconds(tsf::TSFrame, n=1)::TSFrame
```
