```
Results(glacier::G, ifm::IF;
    rgi_id::String = glacier.rgi_id,
    H::Union{Nothing, Vector{Matrix{F}}} = nothing,
    H_glathida::Matrix{F} = glacier.H_glathida,
    H_ref::Union{Nothing, Vector{Matrix{F}}} = nothing,
    S::Union{Nothing, Matrix{F}} = nothing,
    B::Union{Nothing, Matrix{F}} = nothing,
    V::Union{Nothing, Vector{Matrix{F}}} = nothing,
    Vx::Union{Nothing, Vector{Matrix{F}}} = nothing,
    Vy::Union{Nothing, Vector{Matrix{F}}} = nothing,
    V_ref::Union{Nothing, Vector{Matrix{F}}} = nothing,
    Vx_ref::Union{Nothing, Vector{Matrix{F}}} = nothing,
    Vy_ref::Union{Nothing, Vector{Matrix{F}}} = nothing,
    Δx::F = glacier.Δx,
    Δy::F = glacier.Δy,
    lon::Union{Nothing, F} = glacier.cenlon,
    lat::Union{Nothing, F} = glacier.cenlat,
    nx::I = glacier.nx,
    ny::I = glacier.ny,
    t::Union{Vector{F}, Nothing} = nothing,
    tspan::Union{Tuple{F, F}, Nothing} = nothing,
    θ::Union{Nothing,ComponentArray{F}} = nothing,
    loss::Union{Nothing,Vector{F}} = nothing
) where {G <: AbstractGlacier, F <: AbstractFloat, IF <: AbstractModel, I <: Int}
```

Construct a `Results` object for a glacier simulation.

# Arguments

  * `glacier::G`: The glacier object, subtype of `AbstractGlacier`.
  * `ifm::IF`: The model object, subtype of `AbstractModel`.
  * `rgi_id::String`: The RGI identifier for the glacier. Defaults to `glacier.rgi_id`.
  * `H::Union{Nothing, Vector{Matrix{F}}}`: Ice thickness matrices. Defaults to nothing.
  * `H_glathida::Matrix{F}`: Ice thickness from GlaThiDa. Defaults to `glacier.H_glathida`.
  * `H_ref::Union{Nothing, Vector{Matrix{F}}}`: Reference ice thickness. Defaults to nothing.
  * `S::Union{Nothing, Matrix{F}}`: Surface elevation matrix. Defaults to a zero matrix of the same size as `ifm.S`.
  * `B::Union{Nothing, Matrix{F}}`: Bed elevation matrix. Defaults to a zero matrix of the same size as `glacier.B`.
  * `V::Union{Nothing, Vector{Matrix{F}}}`: Velocity magnitude matrix. Defaults to nothing.
  * `Vx::Union{Nothing, Vector{Matrix{F}}}`: Velocity in the x-direction matrix. Defaults to nothing.
  * `Vy::Union{Nothing, Vector{Matrix{F}}}`: Velocity in the y-direction matrix. Defaults to nothing.
  * `V_ref::Union{Nothing, Vector{Matrix{F}}}`: Reference velocity magnitude matrix. Defaults to nothing.
  * `Vx_ref::Union{Nothing, Vector{Matrix{F}}}`: Reference velocity in the x-direction matrix. Defaults to nothing.
  * `Vy_ref::Union{Nothing, Vector{Matrix{F}}}`: Reference velocity in the y-direction matrix. Defaults to nothing.
  * `Δx::F`: Grid spacing in the x-direction. Defaults to `glacier.Δx`.
  * `Δy::F`: Grid spacing in the y-direction. Defaults to `glacier.Δy`.
  * `lon::Union{Nothing, F}`: Longitude of the glacier center. Defaults to `glacier.cenlon`.
  * `lat::Union{Nothing, F}`: Latitude of the glacier center. Defaults to `glacier.cenlat`.
  * `nx::I`: Number of grid points in the x-direction. Defaults to `glacier.nx`.
  * `ny::I`: Number of grid points in the y-direction. Defaults to `glacier.ny`.
  * `tspan::Tuple(F, F)`: Timespan of the simulation.
  * `θ::Union{Nothing, ComponentArray{F}}`: Model parameters. Defaults to `nothing`.
  * `loss::Union{Nothing, Vector{F}}`: Loss values. Defaults to `nothing`.

# Returns

  * `results::Results`: A `Results` object containing the simulation results.
