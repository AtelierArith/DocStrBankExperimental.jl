```julia
show_recorder_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    filename::AbstractString;
    ...
)
show_recorder_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    filename::AbstractString,
    filter_func::Union{Nothing, Function};
    wall_time,
    kwargs...
)

```

```
show_recorder_events(
    ::Type{T},
    filename::AbstractString,
    filter_func::Union{Nothing, Function} = nothing;
    wall_time = false,
    kwargs...,
) where {T <: IS.AbstractRecorderEvent}
```

Tのタイプのイベントをレコーダーファイルに表示します。

# 引数

  * `::Type{T}`: レコーダーイベントタイプ
  * `filename::AbstractString`: レコーダーファイル名
  * `filter_func::Union{Nothing, Function} = nothing`: オプションの関数で、タイプTのイベントを受け取り、Boolを返します。この関数を各イベントに適用し、結果がtrueのイベントのみを返します。
  * `wall_time = false`: trueの場合、wall_timeのタイムスタンプを表示します。
