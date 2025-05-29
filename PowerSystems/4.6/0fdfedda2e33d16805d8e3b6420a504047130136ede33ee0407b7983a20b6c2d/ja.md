```
mutable struct SwitchedAdmittance <: ElectricLoad
    name::String
    available::Bool
    bus::ACBus
    Y::Complex{Float64}
    number_of_steps::Int
    Y_increase::Complex{Float64}
    dynamic_injector::Union{Nothing, DynamicInjection}
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

スイッチングアドミタンスは、アドミタンスを調整するための離散ステップを持っています。

最も一般的には、アドミタンスが結果に与える影響を確認するためにステップを反復する電力フロー研究で使用されます。総アドミタンスは次のように計算されます: `Y` + `number_of_steps` * `Y_increase`

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例: `PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例: `PowerLoad` と `ACBus`）は同じ名前を持つことができます
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンしているか（`false`）を示すインジケーター。利用できないコンポーネントはシミュレーション中に除外されます
  * `bus::ACBus`: このコンポーネントが接続されているバス
  * `Y::Complex{Float64}`: N = 0 の初期アドミタンス
  * `number_of_steps::Int`: （デフォルト: `0`）調整可能なシャントのステップ数
  * `Y_increase::Complex{Float64}`: （デフォルト: `0`）各ステップ増加のアドミタンス増分
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: （デフォルト: `nothing`）アドミタンスに対応する動的注入モデル
  * `services::Vector{Service}`: （デフォルト: `Device[]`）このデバイスが貢献するサービス
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl の内部参照
