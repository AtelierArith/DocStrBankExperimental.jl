```julia
struct ConfigNUTS{K<:BaytesMCMC.KineticEnergy} <: BaytesCore.AbstractConfiguration
```

Default Configuration for NUTS sampler.

# Fields

  * `δ::Float64`: Target Acceptance Rate
  * `max_depth::Int64`: Maximum tree depth.
  * `window::BaytesMCMC.ConfigTuningWindow`: Default size for tuning iterations in each cycle.
  * `energy::BaytesMCMC.KineticEnergy`: Kinetic Energy used in Hamiltonian: GaussianKineticEnergy
  * `difforder::BaytesDiff.DiffOrderOne`: Differentiable order for objective function needed to run proposal step
