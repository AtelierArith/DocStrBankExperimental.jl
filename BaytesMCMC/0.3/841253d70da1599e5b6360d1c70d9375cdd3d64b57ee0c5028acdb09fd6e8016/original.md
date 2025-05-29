```julia
mutable struct StepNumberTune{T<:BaytesCore.UpdateBool}
```

Contains information for number of discretization steps in MCMC algorithm.

# Fields

  * `adaption::BaytesCore.UpdateBool`: If true, number of steps will be adapted.
  * `steps::Int64`: Number of discretization steps.
  * `stepsᵐᵃˣ::Int64`: Maximum number of discretization steps.
  * `∫dt::Float64`: Desired Integration time
