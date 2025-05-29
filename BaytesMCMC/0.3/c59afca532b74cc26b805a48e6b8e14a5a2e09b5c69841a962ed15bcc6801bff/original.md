```julia
struct ConfigMALA <: BaytesCore.AbstractConfiguration
```

Default Configuration for MALA sampler.

# Fields

  * `δ::Float64`: Target Acceptance Rate
  * `window::BaytesMCMC.ConfigTuningWindow`: Default size for tuning iterations in each cycle.
  * `difforder::BaytesDiff.DiffOrderOne`: Differentiable order for objective function needed to run proposal step
