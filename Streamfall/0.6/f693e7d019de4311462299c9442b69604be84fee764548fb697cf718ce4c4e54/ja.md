```
align_time_frame(timeseries::T...)
```

任意の数のDataFrameをそれらの共有期間にサブセットします。

入力と同じ順序でデータのサブセットコピーを返します。

# 例

```julia-repl
julia> climate, streamflow = align_time_frame(climate, streamflow)
```
