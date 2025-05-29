```
mutable struct Simulation{T <: SSDFloat, CS <: AbstractCoordinateSystem} <: AbstractSimulation{T}
```

シミュレーションのすべての部分のコレクション [`SolidStateDetector`](@ref)。

## パラメトリック型

  * `T`: 精度型。
  * `CS`: 座標系（`Cartesian` または `Cylindrical`）。

## フィールド

  * `config_dict::AbstractDict`: シミュレーションを初期化するための辞書（解析された設定ファイル）。
  * `input_units::NamedTuple`: `config_dict` を解析するための単位。
  * `medium::NamedTuple`: 世界の媒体。
  * `detector::Union{SolidStateDetector{T}, Missing}`: シミュレーションの [`SolidStateDetector`](@ref)。
  * `world::World{T, 3, CS}`: シミュレーションの [`World`](@ref)。
  * `q_eff_imp::Union{EffectiveChargeDensity{T}, Missing}`: `detector` の [`Semiconductor`](@ref) における不純物から生じる有効電荷。
  * `imp_scale::Union{ImpurityScale{T}, Missing}`: 不純物密度のスケール（デプレーション処理用のアルファチャネル）。
  * `q_eff_fix::Union{EffectiveChargeDensity{T}, Missing}`: `detector` の [`Passive`](@ref) における固定空間電荷から生じる固定電荷。
  * `ϵ_r::Union{DielectricDistribution{T}, Missing}`: シミュレーションの [`DielectricDistribution`](@ref)。
  * `point_types::Union{PointTypes{T}, Missing}`: シミュレーションの [`PointTypes`](@ref)。
  * `electric_potential::Union{ElectricPotential{T}, Missing}`: シミュレーションの [`ElectricPotential`](@ref)。
  * `weighting_potentials::Vector{Any}`: シミュレーションの `detector` の各 [`Contact`](@ref) に対する [`WeightingPotential`](@ref)。
  * `electric_field::Union{ElectricField{T}, Missing}`: シミュレーションの [`ElectricField`](@ref)。
