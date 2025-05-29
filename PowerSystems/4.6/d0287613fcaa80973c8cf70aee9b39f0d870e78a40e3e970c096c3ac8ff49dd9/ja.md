```
mutable struct DCBus <: Bus
    number::Int
    name::String
    magnitude::Union{Nothing, Float64}
    voltage_limits::Union{Nothing, MinMax}
    base_voltage::Union{Nothing, Float64}
    area::Union{Nothing, Area}
    load_zone::Union{Nothing, LoadZone}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

DCバス

# 引数

  * `number::Int`: 一意のバス識別番号（正の整数）
  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持たなければならず、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます
  * `magnitude::Union{Nothing, Float64}`: `base_voltage`の倍数としての電圧、検証範囲: `voltage_limits`
  * `voltage_limits::Union{Nothing, MinMax}`: `base_voltage`の倍数としての電圧変動の制限
  * `base_voltage::Union{Nothing, Float64}`: kV単位の基準電圧、検証範囲: `(0, nothing)`
  * `area::Union{Nothing, Area}`: （デフォルト: `nothing`）DCバスを含むエリア
  * `load_zone::Union{Nothing, LoadZone}`: （デフォルト: `nothing`）DCバスを含む負荷ゾーン
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照
