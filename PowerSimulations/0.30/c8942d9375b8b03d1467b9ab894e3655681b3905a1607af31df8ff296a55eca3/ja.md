```julia
show_simulation_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    output_dir::AbstractString;
    ...
)
show_simulation_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    output_dir::AbstractString,
    filter_func::Union{Nothing, Function};
    step,
    model,
    wall_time,
    kwargs...
)

```

```
show_simulation_events(
    ::Type{T},
    output_dir::AbstractString,
    filter_func::Union{Nothing,Function} = nothing;
    step = nothing,
    model = nothing,
    wall_time = false,
    kwargs...,
) where { T <: IS.AbstractRecorderEvent}
```

シミュレーション出力ディレクトリ内のタイプ T のすべてのシミュレーションイベントを表示します。

# 引数

  * `::Type{T}`: レコーダーイベントタイプ
  * `output_dir::AbstractString`: シミュレーション出力ディレクトリ
  * `filter_func::Union{Nothing, Function} = nothing`: [`show_recorder_events`](@ref)を参照してください。
  * `step::Int = nothing`: ステップでイベントをフィルタリングします。モデルが渡された場合は必須です。
  * `model::Int = nothing`: モデルでイベントをフィルタリングします。
  * `wall_time = false`: true の場合、wall_time タイムスタンプを表示します。
