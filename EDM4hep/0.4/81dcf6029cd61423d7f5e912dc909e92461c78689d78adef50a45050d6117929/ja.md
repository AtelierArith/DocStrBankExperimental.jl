シミュレートされた一次イオン化

  * 著者: Wenxing Fang, IHEP

# フィールド

  * `cellID::UInt64`: セルID。
  * `time::Float32`: 実験室系における一次イオン化の時間 [ns]。
  * `position::Vector3d`: 実験室系における一次イオン化の位置 [mm]。
  * `type::Int16`: タイプ。
  * `electronCellID::PVector{UInt64}`: セルID。
  * `electronTime::PVector{Float32}`: 実験室系における時間 [ns]。
  * `electronPosition::PVector{Vector3d}`: 実験室系における位置 [mm]。
  * `pulseTime::PVector{Float32}`: 実験室系におけるパルスの時間 [ns]。
  * `pulseAmplitude::PVector{Float32}`: パルスの振幅 [fC]。

# 関係

  * `mcparticle::MCParticle`: イオン化衝突を引き起こした粒子。

# メソッド

  * `setElectronCellID(object::SimPrimaryIonizationCluster, v::AbstractVector{UInt64})`: `electronCellID` ベクターメンバーに値のセットを割り当てる
  * `setElectronTime(object::SimPrimaryIonizationCluster, v::AbstractVector{Float32})`: `electronTime` ベクターメンバーに値のセットを割り当てる
  * `setElectronPosition(object::SimPrimaryIonizationCluster, v::AbstractVector{Vector3d})`: `electronPosition` ベクターメンバーに値のセットを割り当てる
  * `setPulseTime(object::SimPrimaryIonizationCluster, v::AbstractVector{Float32})`: `pulseTime` ベクターメンバーに値のセットを割り当てる
  * `setPulseAmplitude(object::SimPrimaryIonizationCluster, v::AbstractVector{Float32})`: `pulseAmplitude` ベクターメンバーに値のセットを割り当てる
