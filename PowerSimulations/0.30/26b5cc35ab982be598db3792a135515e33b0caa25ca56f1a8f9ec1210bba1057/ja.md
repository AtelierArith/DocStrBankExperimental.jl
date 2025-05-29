```julia
list_simulation_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    output_dir::AbstractString;
    ...
) -> Vector{T} where T<:PowerSimulations.AbstractSimulationStatusEvent
list_simulation_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    output_dir::AbstractString,
    filter_func::Union{Nothing, Function};
    step,
    model_name
) -> Vector{T} where T<:PowerSimulations.AbstractSimulationStatusEvent

```

```
list_simulation_events(
    ::Type{T},
    output_dir::AbstractString,
    filter_func::Union{Nothing, Function} = nothing;
    step = nothing,
    model = nothing,
) where {T <: IS.AbstractRecorderEvent}
```

シミュレーション出力ディレクトリ内のタイプ T のシミュレーションイベントをリストします。

# 引数

  * `output_dir::AbstractString`: シミュレーション出力ディレクトリ
  * `filter_func::Union{Nothing, Function} = nothing`: [`show_simulation_events`](@ref) を参照してください。
  * `step::Int = nothing`: ステップでイベントをフィルタリングします。モデルが渡された場合は必須です。
  * `model::Int = nothing`: モデルでイベントをフィルタリングします。
