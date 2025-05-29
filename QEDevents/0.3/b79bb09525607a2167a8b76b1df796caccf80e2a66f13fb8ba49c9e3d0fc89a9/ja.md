ScatteringProcessDistribution

散乱過程分布からサンプルを描画するための基本タイプ。以下のインターフェース関数を実装する必要があります：

  * `QEDbase.process(d::ScatteringProcessDistribution)`
  * `QEDbase.model(d::ScatteringProcessDistribution)`
  * `QEDbase.phase_space_layout(d::ScatteringProcessDistribution)`
  * [`QEDevents._randmom(rng::AbstractRNG,d::ScatteringProcessDistribution)`](@ref)
