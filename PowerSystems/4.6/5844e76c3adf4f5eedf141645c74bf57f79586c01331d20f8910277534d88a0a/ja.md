```julia
get_time_series_multiple(
    sys::PowerSystems.System;
    ...
) -> Channel{Any}
get_time_series_multiple(
    sys::PowerSystems.System,
    filter_func;
    type,
    name
) -> Channel{Any}

```

初期時間の順序で時間系列のイテレータを返します。

フィルタ関数を渡すことは、メディアから時間系列データを読み取るため、他のフィルタリングパラメータよりもはるかに遅くなる可能性があることに注意してください。

結果に対して `collect` を呼び出すと、配列が得られます。

# 引数

  * `data::SystemData`: システム
  * `filter_func = nothing`: これが真を返す時間系列のみを返します。
  * `type = nothing`: このタイプの時間系列のみを返します。
  * `name = nothing`: この値に一致する時間系列のみを返します。

# 例

```julia
for time_series in get_time_series_multiple(sys)
    @show time_series
end

ts = collect(get_time_series_multiple(sys; type = SingleTimeSeries))
```
