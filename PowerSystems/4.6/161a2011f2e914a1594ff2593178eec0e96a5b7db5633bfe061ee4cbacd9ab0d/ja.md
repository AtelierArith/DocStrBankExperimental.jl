```
mutable struct LoadZone <: AggregationTopology
    name::String
    peak_active_power::Float64
    peak_reactive_power::Float64
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

電力価格分析のための負荷ゾーン。

負荷ゾーンは、ゾーン内の各 [`ACBus`](@ref) または [`DCBus`](@ref) を定義する際に指定できます。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例: `PowerLoad`）はユニークな名前を持たなければなりませんが、異なるタイプのコンポーネント（例: `PowerLoad` と `ACBus`）は同じ名前を持つことができます。
  * `peak_active_power::Float64`: ゾーン内のピークアクティブパワー (MW)
  * `peak_reactive_power::Float64`: ゾーン内のピークリアクティブパワー (MVAR)
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための [*ext*ra dictionary](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl の内部参照
