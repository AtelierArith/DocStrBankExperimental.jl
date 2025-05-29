```
MseedTraceSegment{T}
```

要素タイプ `T` の連続データのセグメント。

# フィールド

  * `starttime::NanosecondDateTime`: 最初のサンプルの日付と時刻。
  * `endtime::NanosecondDateTime`: 最後のサンプルの日付と時刻。
  * `sample_rate::Float64`: サンプル毎秒の名目サンプリングレート。
  * `sample_count::Int64`: トレースカバレッジ内のサンプル数。
  * `data::Vector{T}`: トレースのデータ値。
