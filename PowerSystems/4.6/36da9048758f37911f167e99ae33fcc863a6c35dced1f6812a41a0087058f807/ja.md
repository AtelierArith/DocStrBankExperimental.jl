```
mutable struct Area <: AggregationTopology
    name::String
    peak_active_power::Float64
    peak_reactive_power::Float64
    load_response::Float64
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

制御目的のためのバスのコレクション。

`Area`は、エリア内の各[`ACBus`](@ref)または[`DCBus`](@ref)を定義する際に指定できます。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `peak_active_power::Float64`: (デフォルト: `0.0`) エリア内のピーク有効電力
  * `peak_reactive_power::Float64`: (デフォルト: `0.0`) エリア内のピーク無効電力
  * `load_response::Float64`: (デフォルト: `0.0`) 負荷周波数ダンピングパラメータで、周波数の変化に応じてエリア内の負荷がどれだけ変化するかをモデル化します（MW/Hz）。 [こちらの例。](https://doi.org/10.1109/NAPS50074.2021.9449687)
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータ（緯度や経度など）をユーザーが追加するための[*ext*ra辞書](@ref additional_fields)。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
