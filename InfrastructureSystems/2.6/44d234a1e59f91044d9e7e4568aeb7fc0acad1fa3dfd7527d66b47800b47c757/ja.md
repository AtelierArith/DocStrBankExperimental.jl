```julia
list_recorder_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    filename::AbstractString
) -> Vector{T} where T<:InfrastructureSystems.AbstractRecorderEvent
list_recorder_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    filename::AbstractString,
    filter_func::Union{Nothing, Function}
) -> Vector{T} where T<:InfrastructureSystems.AbstractRecorderEvent

```

filename内のT型のイベントを返します。

# 引数

  * `T`: イベントタイプ
  * `filename::AbstractString`: レコーダーイベントを含むファイル名
  * `filter_func::Union{Nothing, Function} = nothing`: T型のイベントを受け取り、Boolを返すオプションの関数。この関数を各イベントに適用し、結果がtrueのイベントのみを返します。
