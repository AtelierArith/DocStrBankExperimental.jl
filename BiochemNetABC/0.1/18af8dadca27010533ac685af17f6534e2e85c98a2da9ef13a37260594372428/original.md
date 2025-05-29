`volatile_simulate(pm::ParametricModel, p_prior::AbstractVector{Float64})`

A volatile version of `simulate(pm::ParametricModel, p_prior::AbstractVector{Float64})`. The model in `pm` should be of type SynchronizedModel (`typeof(pm.m) <: SynchronizedModel`). It returns `S::StateLHA`, not a trajectory.
