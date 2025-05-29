```
Simulation(model::Model, T::Real, Δt::Real, S_high::Real, S_low::Real, t::AbstractVector{Real})
```

A struct that contains the information of a simulation of a stochastic process.

# Fields

  * `model::Model`: The power spectral density of the process.
  * `T::Real`: The duration of the simulated time series. Note that the time stamps are from 0 to `T`, so the duration is `T`.
  * `Δt::Real`: The sampling period, or minimum time difference between samples.
  * `S_high::Real`: The factor by which the maximum frequency is multiplied for the simulation.
  * `S_low::Real`: The factor by which the minimum frequency is divided for the simulation.
  * `t::AbstractVector{Real}`: The time vector, in this case, the time at which the process is sampled. It is assumed that the time vector is sorted.

# Constructors

  * `Simulation(model::Model, T::Real, Δt::Real, S_high::Real, S_low::Real, t::AbstractVector{Real})`: Constructs a simulation with regular sampling.
  * `Simulation(model::Model, T::Real, Δt::Real)`: Constructs a simulation with regular sampling, and sets `S_high` and `S_low` to 10.0.
  * `Simulation(model::Model, T::Real, Δt::Real, S_high::Real, S_low::Real)`: Constructs a simulation with the given parameters.
  * `Simulation(model::Model, t::AbstractVector{Real}, S_high::Real, S_low::Real)`: Constructs a simulation with sampling pattern given by `t`.
  * `Simulation(model::Model, t::AbstractVector{Real})`: Constructs a simulation with sampling pattern given by `t`, and sets `S_high` and `S_low` to 10.0.
