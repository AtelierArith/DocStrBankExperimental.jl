Constructs `SurfaceVelocityData` using data from Rabatel et. al (2023) with the given parameters, including default ones.

function SurfaceVelocityData(;     x::Union{Vector{F}, Nothing} = nothing,     y::Union{Vector{F}, Nothing} = nothing,     lat::Union{Vector{F}, Nothing} = nothing,     lon::Union{Vector{F}, Nothing} = nothing,     vx::Union{Vector{Matrix{F}}, Nothing} = nothing,     vy::Union{Vector{Matrix{F}}, Nothing} = nothing,     vabs::Union{Vector{Matrix{F}}, Nothing} = nothing,     vx*error::Union{Vector{F}, Nothing} = nothing,     vy*error::Union{Vector{F}, Nothing} = nothing,     vabs*error::Union{Vector{F}, Nothing} = nothing,     date::Union{Vector{DateTime}, Nothing} = nothing,     date1::Union{Vector{DateTime}, Nothing} = nothing,     date2::Union{Vector{DateTime}, Nothing} = nothing,     date*error::Union{Vector{Day}, Vector{Millisecond}, Nothing} = nothing,     isGridGlacierAligned::Bool = false, ) where {F <: AbstractFloat}

Constructor for ice surface velocity data based on Rabatel et. al (2023).

Important remarks:

  * The error in velocity is unique per timestamp, rather than being pixel distributed.
  * The error in the absolute velocities `vabs_error` is overestimated.

References:     - Rabatel, A., Ducasse, E., Millan, R. & Mouginot, J.     Satellite-Derived Annual Glacier Surface Flow Velocity Products for the European Alps,     2015–2021.     Data 8, 66 (2023).
