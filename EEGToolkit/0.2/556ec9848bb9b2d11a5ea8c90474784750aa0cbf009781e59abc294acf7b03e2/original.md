`freq_band(spec::Union{PSD}, lower::AbstractFloat, upper::AbstractFloat)`

Given a `PSD`, returns a `Vector{<:AbstractFloat}` with the powers within the frequency band `[lower, upper]`.
