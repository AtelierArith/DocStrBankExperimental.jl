```julia
struct ConfigHMC{K<:BaytesMCMC.KineticEnergy, S<:BaytesMCMC.ConfigStepnumber} <: BaytesCore.AbstractConfiguration
```

Default Configuration for HMC sampler.

# Fields

  * `δ::Float64`: Target Acceptance Rate
  * `window::BaytesMCMC.ConfigTuningWindow`: Default size for tuning iterations in each cycle.
  * `energy::BaytesMCMC.KineticEnergy`: Kinetic Energy used in Hamiltonian: GaussianKineticEnergy
  * `stepnumber::BaytesMCMC.ConfigStepnumber`: Step Number adaption
  * `difforder::BaytesDiff.DiffOrderOne`: Differentiable order for objective function needed to run proposal step
