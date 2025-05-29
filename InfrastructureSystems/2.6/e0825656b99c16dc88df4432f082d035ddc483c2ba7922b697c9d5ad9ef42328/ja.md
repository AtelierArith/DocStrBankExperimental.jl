```julia
get_time_series_multiple(
    data::InfrastructureSystems.SystemData;
    ...
) -> Channel{Any}
get_time_series_multiple(
    data::InfrastructureSystems.SystemData,
    filter_func;
    type,
    name
) -> Channel{Any}

```

システムに関連付けられた `TimeSeriesData` インスタンスのイテレータを返します。

フィルタ関数を渡すことは、メディアから時系列データを読み取るため、他のフィルタリングパラメータよりもはるかに遅くなる可能性があることに注意してください。

結果に対して `collect` を呼び出すと、配列が得られます。

# 引数

  * `data::SystemData`: システム
  * `filter_func = nothing`: これが真を返す時系列のみを返します。
  * `type = nothing`: このタイプの時系列のみを返します。
  * `name = nothing`: この値に一致する時系列のみを返します。

参照: [`get_time_series_multiple` from an individual component or attribute](@ref get_time_series_multiple(     owner::TimeSeriesOwners,     filter_func = nothing;     type = nothing,     name = nothing, ))
