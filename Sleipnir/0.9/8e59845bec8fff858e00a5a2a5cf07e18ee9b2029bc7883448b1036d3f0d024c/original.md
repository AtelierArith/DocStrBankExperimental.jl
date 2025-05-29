A mutable struct representing a 2D glacier. Notice that all fields can be empty by providing `nothing` as the default value.

/!\ WARNING /!\ `Glacier` objects should not be constructed manually, but rather through the `initialize_glaciers` function.

`Glacier2D{F <: AbstractFloat, I <: Integer}`

# Fields

  * `rgi_id::String`: The RGI (Randolph Glacier Inventory) identifier for the glacier.
  * `name::String`: The name of the glacier if available.
  * `climate::Union{Climate2D, Nothing}`: The climate data associated with the glacier.
  * `H₀::Union{Matrix{F}, Nothing}`: Initial ice thickness matrix.
  * `H_glathida::Matrix{F}`: Ice thickness matrix from the GLATHIDA dataset.
  * `S::Matrix{F}`: Surface elevation matrix.
  * `B::Matrix{F}`: Bedrock elevation matrix.
  * `V::Union{Matrix{F}, Nothing}`: Ice velocity magnitude matrix.
  * `Vx::Union{Matrix{F}, Nothing}`: Ice velocity in the x-direction matrix.
  * `Vy::Union{Matrix{F}, Nothing}`: Ice velocity in the y-direction matrix.
  * `A::Union{F, Nothing}`: Flow law parameter.
  * `C::Union{F, Nothing}`: Sliding law parameter.
  * `n::Union{F, Nothing}`: Flow law exponent.
  * `slope::Union{Matrix{F}, Nothing}`: Surface slope matrix.
  * `dist_border::Union{Matrix{F}, Nothing}`: Distance to the glacier border matrix.
  * `Coords::Union{Dict{String, Vector{Float64}}, Nothing}`: Coordinates dictionary with keys as coordinate names and values as vectors of coordinates.
  * `Δx::F`: Grid spacing in the x-direction.
  * `Δy::F`: Grid spacing in the y-direction.
  * `nx::I`: Number of grid points in the x-direction.
  * `ny::I`: Number of grid points in the y-direction.
  * `cenlon::Union{F, Nothing}`: Longitude of the glacier center.
  * `cenlat::Union{F, Nothing}`: Latitude of the glacier center.
  * `params_projection::Dict{String, Float64}`: Projection parameters that allows mapping the regional grid to global WGS84 coordinates.
  * `thicknessData::Union{ThicknessData, Nothing}`: Thickness data structure that is used to store the reference values.
  * `velocityData::Union{SurfaceVelocityData, Nothing}`: Surface velocity data structure that is used to store the reference values.
