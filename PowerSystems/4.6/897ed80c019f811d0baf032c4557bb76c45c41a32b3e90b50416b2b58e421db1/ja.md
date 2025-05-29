```
mutable struct DynamicInverter{
    C <: Converter,
    O <: OuterControl,
    IC <: InnerControl,
    DC <: DCSource,
    P <: FrequencyEstimator,
    F <: Filter,
} <: DynamicInjection
    name::String
    ω_ref::Float64
    converter::C
    outer_control::O
    inner_control::IC
    dc_source::DC
    freq_estimator::P
    filter::F
    limiter::Union{nothing, OutputCurrentLimiter}
    base_power::Float64
    n_states::Int
    states::Vector{Symbol}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

動的インバータは、位相または電磁過渡シミュレーションにおけるインバータの動的応答をモデル化するために必要なデータを持っています。

動的インバータは、[Converter](@ref)、[Outer Loop Control](@ref OuterControl)、[Inner Loop Control](@ref InnerControl)、[DC Source](@ref DCSource)、[Frequency Estimator](@ref FrequencyEstimator)、および[Filter](@ref)の6つのコンポーネントで構成されています。

これは、動的応答に特有でない発電機のデータをすべて含む[`StaticInjection`](@ref)デバイスに[`add_component!`](@ref add_component!(     sys::System,     dyn_injector::DynamicInjection,     static_injector::StaticInjection;     kwargs..., ))を使用して接続する必要があります。

# 引数

  * `name::String`: インバータの名前。
  * `ω_ref::Float64`: puで設定された周波数リファレンスセットポイント。
  * `converter <: Converter`: PWM変換のためのコンバータモデル。
  * `outer_control <: OuterControl`: [OuterControl](@ref)コントローラモデル。
  * `inner_control <: InnerControl`: [InnerControl](@ref)コントローラモデル。
  * `dc_source <: DCSource`: [DCSource](@ref)モデル。
  * `freq_estimator <: FrequencyEstimator`: [FrequencyEstimator](@ref)（通常は[PLL](@ref P)）モデル。
  * `filter <: Filter`: [Filter](@ref)モデル。
  * `limiter <: Union{nothing, OutputCurrentLimiter}`: （デフォルト: nothing）内部制御[Current Limiter](@ref OutputCurrentLimiter)モデル
  * `base_power::Float64`: （デフォルト: `100.0`）[per unitization](@ref per_unit)のためのユニットの基準電力（MVA）。デフォルトがありますが、ほとんどの場合、`base_power`はこの動的発電機が接続される[`StaticInjection`](@ref)デバイスの`base_power`フィールドと等しくなるように更新する必要があります。
  * `n_states::Int`: （**変更しないでください。**）状態の数（上記の入力に依存します）。
  * `states::Vector{Symbol}`: （**変更しないでください。**）状態のベクター（上記の入力に依存します）。
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照
