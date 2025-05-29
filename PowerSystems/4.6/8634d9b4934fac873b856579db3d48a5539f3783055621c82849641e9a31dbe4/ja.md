```
mutable struct DynamicGenerator{
    M <: Machine,
    S <: Shaft,
    A <: AVR,
    TG <: TurbineGov,
    P <: PSS,
} <: DynamicInjection
    name::String
    ω_ref::Float64
    machine::M
    shaft::S
    avr::A
    prime_mover::TG
    pss::P
    base_power::Float64
    n_states::Int
    states::Vector{Symbol}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

発電機の動的応答を位相または電磁過渡シミュレーションでモデル化するために必要なデータを持つ動的発電機。

動的発電機は、[Machine](@ref)、[Shaft](@ref)、自動電圧調整器（[AVR](@ref)）、[プライムムーバーおよびタービンガバナー](@ref "TurbineGov")、および電力系統安定化装置（[PSS](@ref)）の5つのコンポーネントで構成されています。これは、動的応答に特有でない発電機のデータをすべて含む[`StaticInjection`](@ref)デバイスに[`add_component!`](@ref add_component!(     sys::System,     dyn_injector::DynamicInjection,     static_injector::StaticInjection;     kwargs..., ))を使用して接続する必要があります。

# 引数

  * `name::String`: 発電機の名前。
  * `ω_ref::Float64`: puで設定された周波数リファレンスのセットポイント。
  * `machine <: Machine`: 電磁現象をモデル化するための[Machine](@ref)モデル。
  * `shaft <: Shaft`: 電気機械現象をモデル化するための[Shaft](@ref)モデル。
  * `avr <: AVR`: 励起システムの[AVR](@ref)モデル。
  * `prime_mover <: TurbineGov`: 機械的電力のための[プライムムーバーおよびタービンガバナー](@ref "TurbineGov")モデル。
  * `pss <: PSS`: [PSS](@ref)モデル。
  * `base_power::Float64`: (デフォルト: `100.0`) [単位化](@ref per_unit)のためのユニットの基準電力（MVA）。デフォルトがありますが、ほとんどの場合、`base_power`はこの動的発電機が接続される[`StaticInjection`](@ref)デバイスの`base_power`フィールドと等しくなるように更新する必要があります。
  * `n_states::Int`: (**変更しないでください。**) 状態の数（上記の入力に依存します）。
  * `states::Vector{Symbol}`: (**変更しないでください。**) 状態のベクター（上記の入力に依存します）。
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
