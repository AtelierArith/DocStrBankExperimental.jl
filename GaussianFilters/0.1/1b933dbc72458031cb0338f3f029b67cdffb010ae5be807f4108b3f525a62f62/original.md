```
PHDFilter(γ::GaussianMixture, spawn::Spawn, dyn::Vector{Dynamics},
    meas::Measurement, Ps::Float64, Pd::Float64, κ::Function)
PHDFilter(γ::GaussianMixture, spawn::Spawn, dyn::Dynamics,
    meas::Measurement, Ps::Float64, Pd::Float64, κ::Function)

Sets up a PHD Filter

Arguments:
γ: Birth intensity
spawn: Spawning intensity
dyn: Vector of possible Dynamics models
meas: Measurements
Ps: Survival probability
Pd: Detection probability
```
