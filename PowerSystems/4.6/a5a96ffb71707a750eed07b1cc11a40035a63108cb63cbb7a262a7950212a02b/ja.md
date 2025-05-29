```
mutable struct FixedAdmittance <: ElectricLoad
    name::String
    available::Bool
    bus::ACBus
    Y::Complex{Float64}
    dynamic_injector::Union{Nothing, DynamicInjection}
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

固定アドミタンス。

動的またはAC電力フロー研究で、主に無効電力の供給源として使用されます。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持たなければなりませんが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `bus::ACBus`: このコンポーネントが接続されているバス。
  * `Y::Complex{Float64}`: p.u.での固定アドミタンス（[`SYSTEM_BASE`](@ref per_unit)）。
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （デフォルト：`nothing`）アドミタンスに対応する動的注入モデル。
  * `services::Vector{Service}`: （デフォルト：`Device[]`）このデバイスが貢献するサービス。
  * `ext::Dict{String, Any}`: （デフォルト：`Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照。
