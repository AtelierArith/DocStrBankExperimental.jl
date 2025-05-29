ScatteringProcessDistribution

Base type for sample drawing from scattering process distributions. The following interface functions should be implemented:

  * `QEDbase.process(d::ScatteringProcessDistribution)`
  * `QEDbase.model(d::ScatteringProcessDistribution)`
  * `QEDbase.phase_space_layout(d::ScatteringProcessDistribution)`
  * [`QEDevents._randmom(rng::AbstractRNG,d::ScatteringProcessDistribution)`](@ref)
