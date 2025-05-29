A mutable struct representing a surface velocity data. Notice that all fields can be empty by providing `nothing` as the default value.

`SurfaceVelocityData{F <: AbstractFloat} <: AbstractData`

# Fields

  * `x::Union{Vector{F}, Nothing}`: Easting of observation.
  * `y::Union{Vector{F}, Nothing}`: Northing of observation.
  * `lat::Union{Vector{F}, Nothing}`: Latitude of observation.
  * `lon::Union{Vector{F}, Nothing}`: Longitude of observation.
  * `vx::Union{Vector{Matrix{F}}, Nothing}`: x component of surface velocity.
  * `vy::Union{Vector{Matrix{F}}, Nothing}`: y component of surface velocity.
  * `vabs::Union{Vector{Matrix{F}}, Nothing}`: Absolute ice surface velocity.
  * `vx_error::Union{Vector{F}, Nothing}`: Error in `vx`
  * `vy_error::Union{Vector{F}, Nothing}`: Error in `vy`
  * `vabs_error::Union{Vector{F}, Nothing}`: Error in `vabs`.
  * `date::Union{Vector{DateTime}, Nothing}`: Date of observation (mean of `date1` and `date2`)
  * `date1::Union{Vector{DateTime}, Nothing}`: First date of adquisition.
  * `date2::Union{Vector{DateTime}, Nothing}`: Second date of adquisition.
  * `date_error::Union{Vector{Day}, Vector{Millisecond}, Nothing}`: Error in `date`.
  * `isGridGlacierAligned::Bool`: Whether the data have been gridded to the glacier grid or not.
