Constructs a `Glacier2D` object with the given parameters, including default ones.

```
Glacier2D(;
    rgi_id::Union{String, Nothing} = nothing,
    name::String = "",
    climate::Union{Climate2D, Nothing} = nothing,
    H₀::Union{Matrix{F}, Nothing} = nothing,
    H_glathida::Union{Matrix{F}, Nothing} = nothing,
    S::Union{Matrix{F}, Nothing} = nothing,
    B::Union{Matrix{F}, Nothing} = nothing,
    V::Union{Matrix{F}, Nothing} = nothing,
    Vx::Union{Matrix{F}, Nothing} = nothing,
    Vy::Union{Matrix{F}, Nothing} = nothing,
    A::Union{F, Nothing} = nothing,
    C::Union{F, Nothing} = nothing,
    n::Union{F, Nothing} = nothing,
    slope::Union{Matrix{F}, Nothing} = nothing,
    dist_border::Union{Matrix{F}, Nothing} = nothing,
    Coords::Union{Dict{String, Vector{Float64}}, Nothing} = nothing,
    Δx::Union{F, Nothing} = nothing,
    Δy::Union{F, Nothing} = nothing,
    nx::Union{I, Nothing} = nothing,
    ny::Union{I, Nothing} = nothing,
    cenlon::Union{F, Nothing} = nothing,
    cenlat::Union{F, Nothing} = nothing,
    params_projection::Dict{String, Float64} = Dict{String, Float64}(),
    thicknessData::Union{ThicknessData, Nothing} = nothing,
    velocityData::Union{SurfaceVelocityData, Nothing} = nothing,
) where {F <: AbstractFloat, I <: Integer}
```

# Arguments

  * `rgi_id::String`: The RGI identifier for the glacier.
  * `name::String`: The name of the glacier if available.
  * `climate::Union{Climate2D, Nothing}`: The climate data associated with the glacier.
  * `H₀::Union{Matrix{F}, Nothing}`: Initial ice thickness matrix.
  * `H_glathida::Matrix{F}`: Ice thickness matrix from GLATHIDA.
  * `S::Matrix{F}`: Surface elevation matrix.
  * `B::Matrix{F}`: Bed elevation matrix.
  * `V::Union{Matrix{F}, Nothing}`: Ice velocity magnitude matrix.
  * `Vx::Union{Matrix{F}, Nothing}`: Ice velocity in the x-direction matrix.
  * `Vy::Union{Matrix{F}, Nothing}`: Ice velocity in the y-direction matrix.
  * `A::Union{F, Nothing}`: Flow law parameter.
  * `C::Union{F, Nothing}`: Sliding law parameter.
  * `n::Union{F, Nothing}`: Flow law exponent.
  * `slope::Union{Matrix{F}, Nothing}`: Slope matrix.
  * `dist_border::Union{Matrix{F}, Nothing}`: Distance to border matrix.
  * `Coords::Union{Dict{String, Vector{Float64}}, Nothing}`: Coordinates dictionary with keys "lon" and "lat".
  * `Δx::F`: Grid spacing in the x-direction.
  * `Δy::F`: Grid spacing in the y-direction.
  * `nx::I`: Number of grid points in the x-direction.
  * `ny::I`: Number of grid points in the y-direction.
  * `cenlon::Union{F, Nothing}`: Central longitude of the glacier.
  * `cenlat::Union{F, Nothing}`: Central latitude of the glacier.
  * `params_projection::Dict{String, Float64}`: Projection parameters that allows mapping the regional grid to global WGS84 coordinates.
  * `thicknessData::Union{ThicknessData, Nothing}`: Thickness data structure that is used to store the reference values.
  * `velocityData::Union{SurfaceVelocityData, Nothing}`: Surface velocity data structure that is used to store the reference values.

# Returns

  * A `Glacier2D` object with the specified parameters.
