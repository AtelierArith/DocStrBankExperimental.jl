```
mutable struct Results{F <: AbstractFloat, I <: Int}
```

A mutable struct to store the results of simulations.

# Fields

  * `rgi_id::String`: Identifier for the RGI (Randolph Glacier Inventory).
  * `H::Vector{Matrix{F}}`: Vector of matrices representing glacier ice thickness `H` over time.
  * `H_glathida::Matrix{F}`: Optional matrix for Glathida ice thicknesses.
  * `H_ref::Union{Nothing, Vector{Matrix{F}}}`: Reference data for ice thickness.
  * `S::Matrix{F}`: Glacier surface altimetry.
  * `B::Matrix{F}`: Glacier bedrock.
  * `V::Matrix{F}`: Glacier ice surface velocities.
  * `Vx::Matrix{F}`: x-component of the glacier ice surface velocity `V`.
  * `Vy::Matrix{F}`: y-component of the glacier ice surface velocity `V`.
  * `V_ref::Union{Nothing, Matrix{F}}`: Reference data for glacier ice surface velocities `V`.
  * `Vx_ref::Union{Nothing, Matrix{F}}`: Reference data for the x-component of the glacier ice surface velocity `Vx`.
  * `Vy_ref::Union{Nothing, Matrix{F}}`: Reference data for the y-component of the glacier ice surface velocity `Vy`.
  * `Δx::F`: Grid spacing in the x-direction.
  * `Δy::F`: Grid spacing in the y-direction.
  * `lon::Union{Nothing, F}`: Optional longitude value.
  * `lat::Union{Nothing, F}`: Optional latitude value.
  * `nx::I`: Number of grid points in the x-direction.
  * `ny::I`: Number of grid points in the y-direction.
  * `tspan::Vector{F}`: Time span of the simulation.
  * `θ::Union{Nothing, ComponentArray{F}}`: Machine learning model parameters.
  * `loss::Union{Nothing, Vector{F}}` Vector with evolution of loss function.
